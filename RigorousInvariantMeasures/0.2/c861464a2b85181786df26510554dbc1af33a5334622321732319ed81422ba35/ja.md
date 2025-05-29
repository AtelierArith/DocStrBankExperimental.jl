```
Observable(B::Ulam, ϕ::Function; tol = 2^-10)
```

可観測量 $ϕ$ のウラム離散化を計算し、$||ϕ||_{∞}$ を返します。結果は Observable オブジェクトとして返されます。

例

```jldoctest
julia> using RigorousInvariantMeasures;

julia> B = Ulam(4)
Ulam{LinRange{Float64, Int64}}(LinRange{Float64}(0.0, 1.0, 5))

julia> Observable(B, x->x)
Observable(Ulam{LinRange{Float64, Int64}}(LinRange{Float64}(0.0, 1.0, 5)), Interval{Float64}[[0.125, 0.125], [0.375, 0.375], [0.625, 0.625], [0.875, 0.875]], [0.999734, 1])
```
