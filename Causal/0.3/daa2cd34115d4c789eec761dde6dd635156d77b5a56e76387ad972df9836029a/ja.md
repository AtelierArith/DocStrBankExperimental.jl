```
@def_rode_system ex
```

ここで `ex` は新しい AbstractRODESystem コンポーネントタイプを定義するための式です。使用法は次のとおりです。

```julia
@def_rode_system mutable struct MyRODESystem{T1,T2,T3,...,TN,OP,RH,RO,ST,IP,OP} <: AbstractRODESystem
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

ここで、`MyRODESystem` には `N` パラメータがあります。`MyRODESystem` は `righthandside` と `readout` 関数によって表されます。`state`、`input` および `output` は `MyRODESystem` の初期状態、入力ポートおよび出力ポートです。

!!! warning
    `righthandside` は次のシグネチャを持たなければなりません。

    ```julia
    function righthandside((dx, x, u, t, W, args...; kwargs...)
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
    新しい RODE システムは、正しく機能するために `AbstractRODESystem` のサブタイプでなければなりません。


# 例

```julia
julia> @def_rode_system mutable struct MySystem{RH, RO, IP, OP} <: AbstractRODESystem
           A::Matrix{Float64} = [2. 0.; 0 -2]
           righthandside::RH = (dx, x, u, t, W) -> (dx .= A * x * W)
           readout::RO = (x, u, t) -> x 
           state::Vector{Float64} = rand(2) 
           input::IP = nothing 
           output::OP = Outport(2)
       end

julia> ds = MySystem();
```
