```
@def_dde_system ex
```

ここで `ex` は新しい AbstractDDESystem コンポーネントタイプを定義するための式です。使用法は次のとおりです。

```julia
@def_dde_system mutable struct MyDDESystem{T1,T2,T3,...,TN,OP,RH,RO,ST,IP,OP} <: AbstractDDESystem
    param1::T1 = param1_default                 # オプションフィールド 
    param2::T2 = param2_default                 # オプションフィールド 
    param3::T3 = param3_default                 # オプションフィールド
        ⋮
    paramN::TN = paramN_default                 # オプションフィールド 
    constlags::CL = constlags_default           # 必須フィールド
    depslags::DL = depslags_default             # 必須フィールド
    righthandside::RH = righthandside_function  # 必須フィールド
    history::HST = history_function             # 必須フィールド
    readout::RO = readout_function              # 必須フィールド
    state::ST = state_default                   # 必須フィールド
    input::IP = input_defauult                  # 必須フィールド
    output::OP = output_default                 # 必須フィールド
end
```

ここで、`MyDDESystem` には `N` 個のパラメータがあります。`MyDDESystem` は `righthandside` と `readout` 関数によって表されます。`state`、`input` および `output` は `MyDDESystem` の状態、入力ポートおよび出力ポートです。

!!! warning
    `righthandside` は次のシグネチャを持たなければなりません。

    ```julia
    function righthandside(dx, x, u, t, args...; kwargs...)
        dx .= .... # dx を更新 
    end
    ```

    また、`readout` は次のシグネチャを持たなければなりません。

    ```julia
    function readout(x, u, t)
        y = ...
        return y
    end
    ```


!!! warning
    新しい DDE システムは、正しく機能するために `AbstractDDESystem` のサブタイプでなければなりません。


# 例

```julia
julia> _delay_feedback_system_cache = zeros(1)
1-element Array{Float64,1}:
 0.0

julia> _delay_feedback_system_tau = 1.
1.0

julia> _delay_feedback_system_constlags = [1.]
1-element Array{Float64,1}:
 1.0

julia> _delay_feedback_system_history(cache, u, t) = (cache .= 1.)
_delay_feedback_system_history (generic function with 1 method)

julia> function _delay_feedback_system_rhs(dx, x, h, u, t, 
           cache=_delay_feedback_system_cache, τ=_delay_feedback_system_tau)
           h(cache, u, t - τ)  # キャッシュを更新 
           dx[1] = cache[1] + x[1]
       end
_delay_feedback_system_rhs (generic function with 3 methods)

julia> @def_dde_system mutable struct MyDDESystem{RH, HST, RO, IP, OP} <: AbstractDDESystem
           constlags::Vector{Float64} = _delay_feedback_system_constlags
           depslags::Nothing = nothing
           righthandside::RH = _delay_feedback_system_rhs
           history::HST = _delay_feedback_system_history
           readout::RO = (x, u, t) -> x 
           state::Vector{Float64} = rand(1)
           input::IP = nothing 
           output::OP = Outport(1)
       end

julia> ds = MyDDESystem();
```
