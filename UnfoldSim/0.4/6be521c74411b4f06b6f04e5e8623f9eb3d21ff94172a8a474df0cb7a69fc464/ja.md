```
simulate_component(rng, c::LinearModelComponent, design::AbstractDesign)
```

線形モデルデザイン行列を生成し、係数 `c.β` で重み付けし、結果を指定された基底ベクトルで乗算します。

# 戻り値

  * `Matrix{Float64}`: イベントデータフレーム内の各イベントに対するシミュレートされたコンポーネント。出力の次元は `length(c.basis) x length(design)` です。

# 例

```julia-repl
julia> design = SingleSubjectDesign(; conditions = Dict(:cond => ["natural", "artificial"]));

julia> c = UnfoldSim.LinearModelComponent([0, 1, 1, 0], @formula(0 ~ 1 + cond), [1, 2], Dict());

julia> using StableRNGs

julia> simulate_component(StableRNG(1), c, design)
4×2 Matrix{Float64}:
 0.0  0.0
 3.0  1.0
 3.0  1.0
 0.0  0.0
```
