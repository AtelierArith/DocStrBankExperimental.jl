```
simulate(d::LocalSimulator, task_spec::Union{Circuit, AbstractProgram}, args...; shots::Int=0, inputs::Dict{String, Float64} = Dict{String, Float64}(), kwargs...)
```

`task_spec`の実行を[`LocalSimulator](@ref) `d`のバックエンドを使用してシミュレートします。`args`はバックエンドに提供される追加の引数です。`inputs`は`task_spec`内の任意の[`FreeParameter`](@ref)の値を設定するために使用され、`OpenQasmProgram`の既存の`inputs`フィールドを上書きします。他の`kwargs`はバックエンドシミュレーターに渡されます。[`LocalQuantumTask`](@ref Braket.LocalQuantumTask)を返します。
