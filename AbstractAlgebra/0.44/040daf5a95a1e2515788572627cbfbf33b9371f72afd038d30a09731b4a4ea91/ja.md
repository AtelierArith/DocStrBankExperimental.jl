```
laurent_polynomial_ring(R::Ring, varnames...; cached::Bool = true)
```

基底環 `R` と変数名 `varnames...`、例えば `:x, :y, :z` を与えると、新しい環 $S = R[x, 1/x, y, 1/y, z, 1/z]$ と環の生成元 $x, y, z$ を表すタプル `S, x, y, z` を返します。

デフォルトでは（`cached=true`）、出力 `S` はキャッシュされます。つまり、同じ引数で `laurent_polynomial_ring` が再度呼び出されると、同じ（*同一の*）環が返されます。`cached` を `false` に設定すると、異なる新しい環が返され、キャッシュされることも防止されます。

`varnames...` を指定する多くの方法については、[`polynomial_ring`](@ref) または [`AbstractAlgebra.@varnames_interface`](@ref) の仕様を参照してください。
