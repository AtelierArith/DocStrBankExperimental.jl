```
Tracker(H::AbstractHomotopy;
        options = TrackerOptions(),
        weighted_norm_options = WeightedNormOptions())
```

与えられたホモトピー `H` のためのトラッカーを構築します。このアルゴリズムは、パス $x(t)$ に沿って、4 次までの局所導関数を計算します。`options` については、[`TrackerOptions`](@ref) も参照してください。このアルゴリズムは、距離を測定するために加重無限ノルムを使用します。[`WeightedNorm`](@ref) も参照してください。

[^Tim20]: Timme, S. "Mixed Precision Path Tracking for Polynomial Homotopy Continuation". arXiv:1902.02968 (2020)

## 例

次のシステムを解きたいと思います。

```julia
@var x y t
F = System([x^2 + y^2 - 3, 2x^2 + 0.5x*y + 3y^2 - 2])
```

全体の次数のホモトピーと `Tracker` を使用します。

```julia
# 開始システムとホモトピーを構築
G = System(im * [x^2 - 1, y^2 - 1])
H = StraightLineHomotopy(G, F)
start_solutions = [[1,1], [-1,1], [1,-1], [-1,-1]]
# トラッカーを構築
tracker = Tracker(H)
# 各開始解を個別に追跡
results = track.(tracker, start_solutions)
println("# 成功した: ", count(is_success, results))
```

すべての 4 つのパスを成功裏に追跡したことがわかります。

```
# 成功した: 4
```
