```
hc_solve(g; ntofind=Inf, options...)
```

N人の通常形ゲームのすべての孤立した混合行動ナッシュ均衡を計算します。

この関数は、ナッシュ均衡の非線形補完問題の表現から生じる多項式方程式の系を解くために、`HomotopyContinuation.jl`を使用します。

# 引数

  * `g::NormalFormGame`: N人のNormalFormGameインスタンス。
  * `ntofind=Inf`: 見つけるナッシュ均衡の数。
  * `options...`: `HomotopyContinuation.solve`に渡すオプション引数。たとえば、オプション`seed::UInt32`は、計算中に使用される乱数シードを設定できます。詳細については、`HomotopyContinuation.solve`の[ドキュメント](https://www.juliahomotopycontinuation.org/HomotopyContinuation.jl/stable/solve/)を参照してください。

# 戻り値

  * `::Vector{NTuple{N,Vector{Float64}}}`: 混合行動ナッシュ均衡のベクター。

# 例

McKelveyとMcLennan（1996）の「有限ゲームにおける均衡の計算」における9つのナッシュ均衡を持つ3人の2行動ゲームを考えます：

```julia
julia> Base.active_repl.options.iocontext[:compact] = true;  # 表示する桁数を減らす

julia> g = NormalFormGame((2, 2, 2));

julia> g[1, 1, 1] = [9, 8, 12];

julia> g[2, 2, 1] = [9, 8, 2];

julia> g[1, 2, 2] = [3, 4, 6];

julia> g[2, 1, 2] = [3, 4, 4];

julia> println(g)
2×2×2 NormalFormGame{3, Float64}:
[:, :, 1] =
 [9.0, 8.0, 12.0]  [0.0, 0.0, 0.0]
 [0.0, 0.0, 0.0]   [9.0, 8.0, 2.0]

[:, :, 2] =
 [0.0, 0.0, 0.0]  [3.0, 4.0, 6.0]
 [3.0, 4.0, 4.0]  [0.0, 0.0, 0.0]

julia> NEs = hc_solve(g, show_progress=false)
9-element Vector{Tuple{Vector{Float64}, Vector{Float64}, Vector{Float64}}}:
 ([0.0, 1.0], [0.333333, 0.666667], [0.333333, 0.666667])
 ([1.0, 0.0], [0.0, 1.0], [0.0, 1.0])
 ([0.25, 0.75], [0.5, 0.5], [0.333333, 0.666667])
 ([0.5, 0.5], [0.5, 0.5], [1.0, -7.34684e-40])
 ([0.0, 1.0], [1.0, 0.0], [-2.93874e-39, 1.0])
 ([0.0, 1.0], [0.0, 1.0], [1.0, 0.0])
 ([0.5, 0.5], [0.333333, 0.666667], [0.25, 0.75])
 ([1.0, 4.48416e-44], [1.0, -7.17465e-43], [1.0, -4.48416e-44])
 ([0.25, 0.75], [1.0, 0.0], [0.25, 0.75])

julia> all([is_nash(g, NE) for NE in NEs])
true
```
