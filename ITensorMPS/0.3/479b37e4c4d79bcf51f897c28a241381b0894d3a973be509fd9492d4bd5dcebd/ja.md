```
linkdim(M::MPS, j::Integer)
linkdim(M::MPO, j::Integer)
```

MPSまたはMPOテンソルがサイトjからサイトj+1に接続するリンクまたはボンドの次元を取得します。

リンクインデックスがない場合は、`nothing`を返します。
