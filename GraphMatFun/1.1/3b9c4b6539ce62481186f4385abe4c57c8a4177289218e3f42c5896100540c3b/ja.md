```
normalize!(degopt::Degopt,tp=:row1) -> degopt
```

[`Degopt`](@ref) の係数を、`tp` で指定された方法で正規化します。`tp==:row1` の場合、`degopt` は最初の行が `(0 1) (0 1)` に等しい [`Degopt`](@ref) に変換されます。`tp==:col1` の場合、`Ha` および `Hb` 行列の最初の列はゼロに変換されます。
