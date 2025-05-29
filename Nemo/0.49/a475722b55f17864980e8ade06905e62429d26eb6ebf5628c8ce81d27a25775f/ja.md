```
unramified_extension(Qp::PadicField, d::Int, var::String = "a"; precision::Int=64, cached::Bool=true)
```

与えられた$p$-進体`Qp`の次数$d$の非分岐拡大$K$を返します。$K$の生成元は`var`として表示されます。

$$
K
$$

の要素のデフォルトの絶対精度は`precision`で設定できます。
