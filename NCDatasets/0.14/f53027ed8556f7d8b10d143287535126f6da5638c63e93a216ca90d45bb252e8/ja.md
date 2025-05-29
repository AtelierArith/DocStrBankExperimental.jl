```
isshuffled,isdeflated,deflate_level = deflate(v::Variable)
```

変数 `v` の圧縮情報を返します。shuffle が `true` の場合、シャッフル（バイトインターレース）が有効になります。deflate が `true` の場合、データチャンク（`chunking` を参照）が圧縮レベル `deflate_level` を使用して圧縮されます（0 は圧縮なし、9 は最大圧縮を意味します）。
