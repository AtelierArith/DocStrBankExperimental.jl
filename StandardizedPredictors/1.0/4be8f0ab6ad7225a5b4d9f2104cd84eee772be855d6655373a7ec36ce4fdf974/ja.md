```
struct ZScoredTerm{T,C,S} <: AbstractTerm
```

遅延zスコア化された項。`T<:AbstractTerm`のラッパーで、各要素から`center`を引き、その後`scale`で割ることによって`modelcols`のスケーリングされた値を生成します。

## フィールド

  * `term::T`: ラップされた項。
  * `center::C`: 結果の`modelcols`から引かれる中心値。
  * `scale::S`: 結果の`modelcols`が割られるスケール値。

## 例

指定されたスケールで直接構築:

```
julia> d = (x=collect(1:10), );

julia> t = concrete_term(term(:x), d)
x(continuous)

julia> ts = ZScoredTerm(t, 3, 5)
x(centered: 3 scaled: 5)

julia> hcat(modelcols(t + ts, d)...)
10×2 Matrix{Float64}:
  1.0  -0.4
  2.0  -0.2
  3.0   0.0
  4.0   0.2
  5.0   0.4
  6.0   0.6
  7.0   0.8
  8.0   1.0
  9.0   1.2
 10.0   1.4
```

[`ZScore`](@ref)を介して遅延スケーリングで構築:

```
julia> ts = concrete_term(term(:x), d, ZScore())
x(centered: 5.5 scaled: 3.03)

julia> hcat(modelcols(t + ts, d)...)
10×2 Matrix{Float64}:
  1.0  -1.4863
  2.0  -1.15601
  3.0  -0.825723
  4.0  -0.495434
  5.0  -0.165145
  6.0   0.165145
  7.0   0.495434
  8.0   0.825723
  9.0   1.15601
 10.0   1.4863
```

または、スキーマヒントを介して同様に:

```
julia> sch = schema(d, Dict(:x => ZScore()))
StatsModels.Schema with 1 entry:
  x => x(centered: 5.5 scaled: 3.03)
```
