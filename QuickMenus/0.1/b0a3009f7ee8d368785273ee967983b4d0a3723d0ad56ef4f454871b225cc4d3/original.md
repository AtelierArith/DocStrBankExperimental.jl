```
fzfmenu([indexer,] itr[; prompt=nothing])
```

Select arbitrarily many elements from `itr` using [`fzf`](https://github.com/junegunn/fzf) fuzzy search.  note that `fzf` is run with `--layout=reverse` so that the list is presented in the same order it exists in memory.
