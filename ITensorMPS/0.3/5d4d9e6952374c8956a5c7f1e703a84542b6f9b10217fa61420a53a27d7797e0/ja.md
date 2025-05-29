```
linkind(M::MPS, j::Integer)
linkind(M::MPO, j::Integer)
```

MPSまたはMPOテンソルがサイトjからサイトj+1に接続されているリンクまたはボンドインデックスを取得します。

リンクインデックスがない場合は、`nothing`を返します。
