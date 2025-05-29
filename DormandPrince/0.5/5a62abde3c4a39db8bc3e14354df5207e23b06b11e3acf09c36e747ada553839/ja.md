```
struct SolverIterator{T <: Real}
SolverIterator(solver, times)
```

ソルバーと時間のベクトルを与えると、このイテレータは各時間におけるソルバーの状態を返します。

ソルバーは、与えられた最後の時間からの解を保持するように変更されます。

# 例

```julia
julia> solver = DP5Solver(fcn, 0.0, [0.0])

julia> times = [1.0, 2.0, 3.0]

julia> intermediate_vals = []

julia> for (time, value) in SolverIterator(solver, times)
            push!(intermediate_values, value[])
        end

```
