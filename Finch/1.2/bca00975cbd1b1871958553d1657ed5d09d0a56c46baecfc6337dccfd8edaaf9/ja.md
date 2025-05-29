```
tensor_tree(io::IO, tns; nmax = 2)
```

テンソル `tns` のツリー表現を `io` に出力します。`nmax` は切り捨てる前に表示する最大の子の数の半分です。
