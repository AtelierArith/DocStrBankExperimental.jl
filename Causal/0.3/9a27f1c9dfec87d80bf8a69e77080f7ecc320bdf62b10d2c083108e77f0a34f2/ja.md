```
@def_ode_system ex
```

ここで `ex` は新しい AbstractODESystem コンポーネントタイプを定義するための式です。使用法は次のとおりです：

```julia
@def_ode_system mutable struct MyODESystem{T1,T2,T3,...,TN,OP,RH,RO,ST,IP,OP} <: AbstractODESystem
    param1::T1 = param1_default                     # オプションフィールド 
    param2::T2 = param2_default                     # オプションフィールド 
    param3::T3 = param3_default                     # オプションフィールド
        ⋮
    paramN::TN = paramN_default                     # オプションフィールド 
    righthandside::RH = righthandeside_function     # 必須フィールド
    readout::RO = readout_function                  # 必須フィールド
    state::ST = state_default                       # 必須フィールド
    input::IP = input_default                       # 必須フィールド
    output::OP = output_default                     # 必須フィールド 
end
```

ここで、`MyODESystem` は `N` 個のパラメータを持っています。`MyODESystem` は `righthandside` と `readout` 関数によって表されます。`state`、`input` および `output` は `MyODESystem` の状態、入力ポートおよび出力ポートです。

!!! warning
    `righthandside` は次のシグネチャを持たなければなりません 

    ```julia
    function righthandside(dx, x, u, t, args...; kwargs...)
        dx .= .... # dx を更新 
    end
    ```

    そして `readout` は次のシグネチャを持たなければなりません 

    ```julia
    function readout(x, u, t)
        y = ...
        return y
    end
    ```


!!! warning
    新しい ODE システムは正しく機能するために `AbstractODESystem` のサブタイプでなければなりません。


!!! warning
    新しい ODE システムは可変型でなければなりません。


# 例

```julia
julia> @def_ode_system mutable struct MyODESystem{RH, RO, IP, OP} <: AbstractODESystem 
       α::Float64 = 1. 
       β::Float64 = 2. 
       righthandside::RH = (dx, x, u, t, α=α) -> (dx[1] = α * x[1] + u[1](t))
       readout::RO = (x, u, t) -> x
       state::Vector{Float64} = [1.]
       input::IP = Inport(1) 
       output::OP = Outport(1) 
       end

julia> ds = MyODESystem();

julia> ds.input 
1-element Inport{Inpin{Float64}}:
 Inpin(eltype:Float64, isbound:false)
```
