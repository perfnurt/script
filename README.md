# Scripts
Various scripts I typically use everywhere I set up a development environment.

## Git aliases
Things to put into `~/.gitconfig`

```
[alias]
    aliases = !git config --get-regexp '^alias' 
    br = branch
    co = checkout
    com = commit -m
    cob = checkout -b
    last = log -1 HEAD
    local-branches = !git branch -vv | cut -c 3- | awk '$3 !~/\\[/ { print $1 }'
    delete-local = !git local-branches | xargs -r git branch -D
    st = status
    push-new = !git push -u origin $(git rev-parse --abbrev-ref HEAD)
    merged = !git branch --merged | egrep -v '(^\\*|master)'
    delete-merged = !git merged | xargs -r git branch -D
    recent !git reflog | egrep -io 'moving from ([^[:space:]]+)' | awk '{ print $3 }' | awk ' !x[$0]++' | head -n15
```
