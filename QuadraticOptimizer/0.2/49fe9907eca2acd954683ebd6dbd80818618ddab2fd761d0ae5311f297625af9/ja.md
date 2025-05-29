```
optimize_qim!(f, ps::Vector{<:SVector{D, <:Real}}, fs::Vector{<:Real}, n_iter::Integer) -> ps, fs
```

関数 `f` を二次補間法 (QIM) を使用して最適化します。

# 引数

  * `f`: 最適化される目的関数。
  * `ps`: `f` が評価された $\mathbb{R}^D$ の点のベクトル。このベクトルは最適化プロセス中にインプレースで更新されます。
  * `fs`: `ps` の点に対応する関数値のベクトル。このベクトルは最適化プロセス中にインプレースで更新されます。
  * `n_iter`: 最適化の反復回数。実行後、`ps` の長さは `N + n_iter` になります。ここで、`N = length(ps)` は実行前の長さです。

!!! note
    QIM の各ステップでは、`ps` と `fs` の最後の `M` (`==((D+2)*(D+1)/2)`) 点が二次関数で補間に使用されます。この方法は、点と関数値を反復的に洗練し、最適化プロセスから得られた `n_iter` の追加点で `ps` と `fs` を拡張します。


# 例

```jldoctest
julia> using QuadraticOptimizer, StaticArrays, Random

julia> Random.seed!(42);

julia> f(p) = p[1]^2 + sin(p[1]) + 1.5p[2]^2 + sinh(p[2]) - p[1]*p[2]/5
f (generic function with 1 method)

julia> ps_init = [@SVector rand(2) for _ in 1:6]
6-element Vector{SVector{2, Float64}}:
 [0.6293451231426089, 0.4503389405961936]
 [0.47740714343281776, 0.7031298490032014]
 [0.6733461456394962, 0.16589443479313404]
 [0.6134782250008441, 0.6683403279577278]
 [0.4570310908017041, 0.2993652953937611]
 [0.6611433726193705, 0.6394313620423493]

julia> ps = copy(ps_init);

julia> fs = f.(ps);

julia> optimize_qim!(f, ps, fs, 20);
```
