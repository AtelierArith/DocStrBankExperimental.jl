```
struct ProblemState
function ProblemState(; u = nothing, p = nothing, t = nothing, h = nothing)
```

値プロバイダ構造体で、[`getsym`](@ref)または[`setsym`](@ref)によって返される関数の引数として使用できます。状態ベクトル、パラメータオブジェクト、現在の時間を格納し、[`state_values`](@ref)、[`parameter_values`](@ref)、[`current_time`](@ref)、[`set_state!`](@ref)、[`set_parameter!`](@ref)への呼び出しを含まれるオブジェクトに転送します。

`h`キーワードを使用して履歴関数を提供することができ、これは[`get_history_function`](@ref)で返されます。
