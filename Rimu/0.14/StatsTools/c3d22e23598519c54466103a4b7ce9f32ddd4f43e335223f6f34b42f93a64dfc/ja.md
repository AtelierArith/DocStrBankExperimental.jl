```
val_and_errs(x; n=1, p=nothing, name=:val) -> (;val, val_l, val_u)
```

不確かな値 `x` の中央値と下限および上限の誤差バーを `NamedTuple` として返します。これはプロットスクリプトに便利です。区間 `[val - val_l, val + val_u]` は、レベル `n*σ` または確率 `p` の信頼区間を表します。`p` を設定すると `n` が上書きされます。 [`MonteCarloMeasurements`](https://github.com/baggepinnen/MonteCarloMeasurements.jl) と [`Measurements`](https://github.com/JuliaPhysics/Measurements.jl) をサポートしています。 `NamedTuple` の名前は `name` で変更できます。

**例:**

```jldoctest
julia> results = [blocking_analysis(i:0.1:2i+20) for i in 1:3]; # モック結果

julia> v = val_and_errs.(results, name="res"); # 標準誤差を持つ NamedTuple のベクトル

julia> DataFrame(v)
3×3 DataFrame
 Row │ res      res_l    res_u
     │ Float64  Float64  Float64
─────┼───────────────────────────
   1 │    11.5  1.7282   1.7282
   2 │    13.0  1.7282   1.7282
   3 │    14.5  1.78885  1.78885
```

[`NamedTuple`](@ref), [`val`](@ref), [`errs`](@ref), [`BlockingResult`](@ref), [`RatioBlockingResult`](@ref) を参照してください。
