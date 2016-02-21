# git-remote-encfs

Just a naive attempt at taking git's `git-remote-testgit` example and
wrapping it in EncFS.

## Installation

Copy `git-remote-encfs` somewhere into your `$PATH` and make sure it
is executable.

## Usage

Simple as

    git remote add encfs encfs::$PATH_TO_REPO
    git encfs push master

`$PATH_TO_REPO` must be a full path to where you want this stored.
`git-remote-encfs` will ensure two directories exist and will create
them if not:
* `$PATH_TO_REPO`
* `${PATH_TO_REPO}-private`

The `-private` directory will contain your encfs directory while
`$PATH_TO_REPO` will be the decrypted directory.

If the directories do not exist, then you will prompted to create an
encfs password.

For now, this script will always unmount your encfs when it finishes,
so every time you use it, it will prompt for a password.

This is an example of how I am using it

    git remote add encfs \
        encfs::$HOME/Dropbox/.secret-repos/git-remote-encfs
    git push encfs master

