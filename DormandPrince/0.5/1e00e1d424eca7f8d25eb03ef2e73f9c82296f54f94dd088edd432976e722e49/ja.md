```
integrate!(solver, time)
```

`solver`の一部であるODE問題を終了時間`time`まで統合します。`solver`は`DP5Solver`または`DP8Solver`タイプであることができます。

`solver`は、時間`time`における解と`solver`の状態を保持するように変更され、後の時間に対する`integrate!`の呼び出しを通じて、将来の終了時間への効率的な統合が可能になります。

# 例

```julia
julia> function fcn(x, y, f)
            f[1] = 0.85y[1]
        end

julia> solver = DP5Solver(fcn, 0.0, [19.0])

# 初期時間0.0から1.0まで統合
julia> integrate!(solver, 1.0)

# 最後の時間1.0から2.0まで統合
julia> integrate!(solver, 2.0)

# Solverオブジェクトは現在2.0における解と状態を保持しています
julia> get_current_state(solver)
```
