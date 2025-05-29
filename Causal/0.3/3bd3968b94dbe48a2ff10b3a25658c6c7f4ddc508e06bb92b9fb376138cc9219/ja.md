```
@def_discrete_system ex
```

ここで `ex` は新しい AbstractDiscreteSystem コンポーネントタイプを定義するための式です。使用法は次のとおりです。

```julia
@def_discrete_system mutable struct MyDiscreteSystem{T1,T2,T3,...,TN,OP,RH,RO,ST,IP,OP} <: AbstractDiscreteSystem
    param1::T1 = param1_default                 # オプションフィールド 
    param2::T2 = param2_default                 # オプションフィールド 
    param3::T3 = param3_default                 # オプションフィールド
        ⋮
    paramN::TN = paramN_default                 # オプションフィールド 
    righthandside::RH = righthandside_function  # 必須フィールド
    readout::RO = readout_function              # 必須フィールド
    state::ST = state_default                   # 必須フィールド
    input::IP = input_default                   # 必須フィールド
    output::OP = output_default                 # 必須フィールド 
end
```

ここで、`MyDiscreteSystem` には `N` のパラメータがあります。`MyDiscreteSystem` は `righthandside` と `readout` 関数によって表されます。`state`、`input` および `output` は `MyDiscreteSystem` の状態、入力ポートおよび出力ポートです。

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
    新しい離散システムは、正しく機能するために `AbstractDiscreteSystem` のサブタイプでなければなりません。


# 例

```julia
julia> @def_discrete_system mutable struct MyDiscreteSystem{RH, RO, IP, OP} <: AbstractDiscreteSystem 
       α::Float64 = 1. 
       β::Float64 = 2. 
       righthandside::RH = (dx, x, u, t, α=α) -> (dx[1] = α * x[1] + u[1](t))
       state::Vector{Float64} = [1.]
       readout::RO = (x, u, t) -> x
       input::IP = Inport(1) 
       output::OP = Outport(1) 
       end

julia> ds = MyDiscreteSystem();

julia> ds.input 
1-element Inport{Inpin{Float64}}:
 Inpin(eltype:Float64, isbound:false)
```
