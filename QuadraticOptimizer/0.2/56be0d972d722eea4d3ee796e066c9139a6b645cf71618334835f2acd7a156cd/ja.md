```
optimize_qfm(f, ps_init::Vector{<:SVector{D, <:Real}}, fs_init::Vector{<:Real}, n_iter::Integer) -> ps, fs
```

関数 `f` を二次フィッティング法 (QFM) を使用して最適化します。

# 引数

  * `f`: 最適化される目的関数。
  * `ps_init`: `f` が評価された $\mathbb{R}^D$ の点のベクトル。
  * `fs_init`: `ps_init` の点に対応する関数値のベクトル。
  * `n_iter`: 最適化の反復回数。実行後、`ps` の長さは `N + n_iter` になります。ここで、`N = length(ps)` は実行前の値です。

!!! note
    QFM の各ステップでは、`ps` と `fs` の最後の `N` 点が二次関数をフィットさせるために使用されます。この手法は、最適化プロセスから得られた `n_iter` の追加点で `ps` と `fs` を拡張しながら、点と関数値を反復的に洗練させます。


# 例

```jldoctest
julia> using QuadraticOptimizer, StaticArrays, Random

julia> Random.seed!(42);

julia> f(p) = p[1]^2 + sin(p[1]) + 1.5p[2]^2 + sinh(p[2]) - p[1]*p[2]/5
f (generic function with 1 method)

julia> ps_init = [@SVector rand(2) for _ in 1:10]
10-element Vector{SVector{2, Float64}}:
 [0.6293451231426089, 0.4503389405961936]
 [0.47740714343281776, 0.7031298490032014]
 [0.6733461456394962, 0.16589443479313404]
 [0.6134782250008441, 0.6683403279577278]
 [0.4570310908017041, 0.2993652953937611]
 [0.6611433726193705, 0.6394313620423493]
 [0.34264792290134793, 0.2678704383989201]
 [0.515871408349502, 0.09002301604339691]
 [0.27265744579429385, 0.191562202596938]
 [0.4235912564725989, 0.4847023673932017]

julia> ps, fs = optimize_qfm(f, ps_init, f.(ps_init), 20);
```
