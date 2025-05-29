```
entropy_permutation(x; τ = 1, m = 3, base = 2)
```

`x`の順序`m`の順列エントロピーを遅延/ラグ`τ`で計算します。この関数は単に次の便利な呼び出しです：

```julia
est = OrdinalPatterns(; m, τ)
information(Shannon(base), est, x)
```

詳細については[`OrdinalPatterns`](@ref)を参照してください。同様に、重み付き/振幅に配慮したバージョンには[`WeightedOrdinalPatterns`](@ref)や[`AmplitudeAwareOrdinalPatterns`](@ref)を使用できます。
