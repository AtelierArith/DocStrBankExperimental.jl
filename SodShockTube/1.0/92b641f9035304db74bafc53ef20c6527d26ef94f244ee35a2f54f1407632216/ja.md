```
solve(s::ShockTubeProblem, x_arr)
```

与えられたショックチューブ問題を指定された x 位置で解きます。

# 戻り値

positions: 領域の説明的な名前を x 座標にマッピングする `Dictionary`

regions: 領域 ("Region 1", "Region 2" など) をショックチューブ解における熱力学的状態 (ρ, p, u) にマッピングする `Dictionary`

values: x 座標、密度、圧力、停滞エネルギーを含む `NamedTuple` (;x, ρ, p, e)

# 例

```jldoctest;setup = :(using SodShockTube) julia> problem = ShockTubeProblem(     geometry = (0.0, 1.0, 0.5),     left*state = (ρ = 1.0, u = 0.0, p = 1.0),     right*state = (ρ = 0.125, u = 0.0, p = 0.1),     t = 0.1,     γ = 1.4 );

julia> xs = LinRange(0.0, 1.0, 500);

julia> positions, regions, values = solve(problem, xs);

julia> positions Dict{String, Float64} with 4 entries:   "Shock"                 => 0.850431   "Foot of rarefaction"   => 0.485945   "Head of rarefaction"   => 0.263357   "Contact Discontinuity" => 0.685491

julia> regions Dict{String, Any} with 5 entries:   "Region 5" => (0.1, 0.125, 0.0)   "Region 1" => (1.0, 1.0, 0.0)   "Region 4" => (0.30313, 0.265574, 0.927453)   "Region 3" => (0.30313, 0.426319, 0.927453)   "Region 2" => "RAREFACTION"
```
