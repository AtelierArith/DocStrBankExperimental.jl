```
contract(X,Y)
contract(X,indX,Y,indY[,perm])
contract(X::TensorCell)
```

テンソルの収束積。配列 X の indX モードを配列 Y の indY モードに収束させ、結果をベクトル perm によって置換します。デフォルト: indX=[ndims(X)], indY=[1]。
