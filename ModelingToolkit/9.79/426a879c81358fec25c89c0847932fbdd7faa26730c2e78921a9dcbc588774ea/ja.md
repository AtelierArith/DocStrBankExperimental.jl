```julia
generate_factorized_W(sys::AbstractSystem, dvs = unknowns(sys), ps = parameters(sys),
                      expression = Val{true}; sparse = false, kwargs...)
```

システムの因子化された W 行列のための関数を生成します。追加の引数は内部の [`build_function`](@ref) 呼び出しへの引数を制御します。
