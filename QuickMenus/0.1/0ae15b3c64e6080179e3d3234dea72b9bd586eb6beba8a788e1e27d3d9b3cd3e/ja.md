```
fzfmenu([indexer,] itr[; prompt=nothing])
```

`itr`から要素を選択するには、[`fzf`](https://github.com/junegunn/fzf) ファジー検索を使用します。`fzf`は`--layout=reverse`オプションで実行されるため、リストはメモリ内に存在するのと同じ順序で表示されます。
