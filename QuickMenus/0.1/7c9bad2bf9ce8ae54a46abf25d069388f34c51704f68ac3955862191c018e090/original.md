```
quickmenu([indexer, ℳ,] itr;
          message="", cursor=1, charset=:unicode, kw...)
```

Presents the user with a terminal menu for selecting elements from the iterable `itr`.

The aliases `qm` (for single selection) or `qmm` for multiple selections are provided by `QuickMenus`.

## Arguments

  * `itr`: the iterable to select elements from.
  * `indexer`: Function used for indexing the iterable `itr`. `getindex`   by default
  * `ℳ`: the type of terminal menu, `RadioMenu` or `MultiSelectMenu`.
  * `message`: message to display before the selection menu.
  * `cursor`: Initial cursor position.
  * `charset`: The character set to use for the terminal menu.
  * `kw`: additional keyword arguments are provided to the terminal menu   constructor `ℳ`.
