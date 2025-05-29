```
struct ScaledTerm{T,S} <: AbstractTerm
```

遅延スケーリングされた項。 `T<:AbstractTerm` のラッパーで、各要素を `scale` で割ることによってスケーリングされた値を生成します。

## フィールド

  * `term::T`: ラップされた項。
  * `scale::S`: 結果の `modelcols` が割られるスケール値。

## 例

指定されたスケールで直接構築：

```
julia> d = (x=collect(1:10), );

julia> t = concrete_term(term(:x), d)
x(continuous)

julia> ts = ScaledTerm(t, 5)
x(scaled: 5)

julia> hcat(modelcols(t + ts, d)...)
10×2 Matrix{Float64}:
  1.0  0.2
  2.0  0.4
  3.0  0.6
  4.0  0.8
  5.0  1.0
  6.0  1.2
  7.0  1.4
  8.0  1.6
  9.0  1.8
 10.0  2.0
```

[`Scale`](@ref) を介して遅延スケーリングで構築：

```
julia> ts = concrete_term(term(:x), d, Scale())
x(scaled: 3.03)

julia> hcat(modelcols(t + ts, d)...)
10×2 Matrix{Float64}:
  1.0  0.330289
  2.0  0.660578
  3.0  0.990867
  4.0  1.32116
  5.0  1.65145
  6.0  1.98173
  7.0  2.31202
  8.0  2.64231
  9.0  2.9726
 10.0  3.30289
```

または、スキーマヒントを介して同様に：

```
julia> sch = schema(d, Dict(:x => Scale()))
StatsModels.Schema with 1 entry:
  x => scale(x, 3.03)
```
