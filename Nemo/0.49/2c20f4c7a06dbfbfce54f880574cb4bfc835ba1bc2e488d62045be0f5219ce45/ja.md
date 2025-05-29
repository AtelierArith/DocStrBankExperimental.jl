```
qadic_field(p::Integer, d::Int, var::String = "a"; precision::Int=64, cached::Bool=true, check::Bool=true)
qadic_field(p::ZZRingElem, d::Int, var::String = "a"; precision::Int=64, cached::Bool=true, check::Bool=true)
```

与えられた素数 $p$ の $p$-進体の次数 $d$ の非分岐拡大 $K$ を返します。$K$ の生成元は `var` として表示されます。

$$
K
$$

の要素のデフォルトの絶対精度は `precision` で設定できます。

詳細は [`unramified_extension`](@ref) を参照してください。
