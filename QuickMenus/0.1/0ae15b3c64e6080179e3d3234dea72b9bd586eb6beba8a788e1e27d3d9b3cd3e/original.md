```
fzfmenu([indexer,] itr[; prompt=nothing])
```

Select an element from `itr` using [`fzf`](https://github.com/junegunn/fzf) fuzzy search.  Note that `fzf` is run with `--layout=reverse` so that the list is presented in the same order as it exists in memory.
