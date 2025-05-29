```
RootSolvers
```

非線形方程式の根を解くための関数を含みます。[`find_zero`](@ref)を参照してください。

## 例

```julia
julia> using RootSolvers

julia> sol = find_zero(x -> x^2 - 100^2,
                       SecantMethod{Float64}(0.0, 1000.0),
                       CompactSolution());

julia> sol
CompactSolutionResults{Float64}:
├── ステータス: 収束
└── 根: 99.99999999994358

julia> sol.root
99.99999999994358
```
