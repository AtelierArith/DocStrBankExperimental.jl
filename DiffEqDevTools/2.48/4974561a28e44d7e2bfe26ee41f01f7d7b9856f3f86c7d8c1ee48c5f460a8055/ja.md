```
stability_region(z, alg::AbstractODEAlgorithm)
```

アルゴリズム `alg` における `z` での安定性関数を計算します。可能な埋め込み法の安定性領域は、このメソッドを使用して計算することはできません。

暗黙的手法を使用する場合、`z` の値が安定性領域の外にあるときに収束の問題が発生する可能性があります。例えば、

```julia-repl
julia> typemin(Float64)
-Inf

julia> stability_region(typemin(Float64), ImplicitEuler())
┌ Warning: Newton steps could not converge and algorithm is not adaptive. Use a lower dt.

julia> nextfloat(typemin(Float64))
-1.7976931348623157e308

julia> stability_region(nextfloat(typemin(Float64)), ImplicitEuler())
0.0
```
