```
integrate!(callback, solver, times)
```

`solver`の一部であるODE問題を、終了時刻`times`まで統合し、各時刻での時間と解に対してコールバックを適用します。`solver`は`DP5Solver`または`DP8Solver`タイプであることができます。

すべての時刻の終了時に、ソルバーは`times`の最後の時刻における解とソルバーの状態を保持します。

# 例

```julia
julia> function fcn(x, y, f)
            f[1] = 0.85y[1]
        end

julia> times = [1.0, 1.1, 1.9, 2.4]

julia> solver = DP5Solver(fcn, 0.0, [19.0])

julia> intermediate_values = []

julia> integrate!(solver, times) do time, val
            push!(intermediate_values, val[])
        end
```
