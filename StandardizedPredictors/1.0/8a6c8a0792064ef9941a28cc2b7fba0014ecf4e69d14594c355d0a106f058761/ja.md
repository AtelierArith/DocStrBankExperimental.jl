```
struct CenteredTerm{T,C} <: AbstractTerm
```

遅延中心化項。`T<:AbstractTerm` のラッパーで、ラップされた項から生成された各要素から `center` を引くことで `modelcols` によって中心化された値を生成します。

## フィールド

  * `term::T`: ラップされた項。
  * `center::C`: 結果の `modelcols` から引かれる中心値。

## 例

指定された中心で直接構築:

```
julia> d = (x=collect(1:10), );

julia> t = concrete_term(term(:x), d)
x(continuous)

julia> tc = CenteredTerm(t, 5)
x(centered: 5)

julia> hcat(modelcols(t + tc, d)...)
10×2 Matrix{Int64}:
  1  -4
  2  -3
  3  -2
  4  -1
  5   0
  6   1
  7   2
  8   3
  9   4
 10   5
```

[`Center`](@ref) を介して遅延中心化で構築:

```
julia> tc = concrete_term(term(:x), d, Center())
center(x, 5.5)

julia> hcat(modelcols(t + tc, d)...)
10×2 Matrix{Float64}:
  1.0  -4.5
  2.0  -3.5
  3.0  -2.5
  4.0  -1.5
  5.0  -0.5
  6.0   0.5
  7.0   1.5
  8.0   2.5
  9.0   3.5
 10.0   4.5
```

または、スキーマヒントを介して同様に:

```
julia> sch = schema(d, Dict(:x => Center()))
StatsModels.Schema with 1 entry:
  x => center(x, 5.5)
```
