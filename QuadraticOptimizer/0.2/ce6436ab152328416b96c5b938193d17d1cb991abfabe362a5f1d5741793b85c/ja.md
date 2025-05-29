```
optimize_qim(f, xs_init::Vector{<:Real}, n_iter::Integer) -> xs, fs
```

関数 `f` を二次補間法 (QIM) を使用して最適化します。

# 引数

  * `f`: 最適化される目的関数。
  * `xs_init`: `f` が評価された $\mathbb{R}^D$ の点のベクトル。
  * `n_iter`: 最適化の反復回数。実行後、`xs` の長さは `N + n_iter` になります。ここで、`N = length(xs)` は実行前の長さです。

!!! note
    QIM の各ステップでは、`xs` と `fs` の最後の `3` 点が二次関数で補間するために使用されます。この方法は、点と関数値を反復的に洗練させ、最適化プロセスから得られた `n_iter` の追加点で `xs` と `fs` を拡張します。


# 例

```jldoctest
julia> using QuadraticOptimizer

julia> f(x) = sin(x) + x^2/10  # 最小化する関数
f (generic function with 1 method)

julia> xs_init = [1.2, 0.1, -2.2]  # 初期点 (放物線を構成するために3点が必要)
3-element Vector{Float64}:
  1.2
  0.1
 -2.2

julia> xs = copy(xs_init)  # 初期点を保持
3-element Vector{Float64}:
  1.2
  0.1
 -2.2

julia> xs, fs = optimize_qim(f, xs, 10);  # 10ステップ最適化
```
