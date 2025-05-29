```
penalty!(mpo,lambda,psi[,compress=])
```

ハミルトニアン（`mpo`）にペナルティを追加します。形式は H0 + `lambda` * |`psi`><`psi`| です。結果の波動関数を圧縮するためのトグルを切り替えます。

関連情報: [`penalty`](@ref)
