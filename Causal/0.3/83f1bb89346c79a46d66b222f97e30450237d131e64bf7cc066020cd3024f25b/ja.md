```
@def_sde_system ex
```

ここで `ex` は新しい AbstractSDESystem コンポーネントタイプを定義するための式です。使用法は次のとおりです。

```julia
@def_sde_system mutable struct MySDESystem{T1,T2,T3,...,TN,OP,RH,RO,ST,IP,OP} <: AbstractSDESystem
    param1::T1 = param1_default                 # オプションフィールド 
    param2::T2 = param2_default                 # オプションフィールド 
    param3::T3 = param3_default                 # オプションフィールド
        ⋮
    paramN::TN = paramN_default                 # オプションフィールド 
    drift::DR = drift_function                  # 必須フィールド
    diffusion::DF = diffusion_function          # 必須フィールド
    readout::RO = readout_functtion             # 必須フィールド
    state::ST = state_default                   # 必須フィールド
    input::IP = input_default                   # 必須フィールド
    output::OP = output_default                 # 必須フィールド
end
```

ここで、`MySDESystem` は `N` 個のパラメータを持ちます。`MySDESystem` は `drift`、`diffusion`、および `readout` 関数によって表されます。`state`、`input`、および `output` は `MySDESystem` の初期状態、入力ポート、および出力ポートです。

!!! warning
    `drift` は次のシグネチャを持たなければなりません。

    ```julia
    function drift((dx, x, u, t, args...; kwargs...)
        dx .= .... # dx を更新
    end
    ```

    また、`diffusion` は次のシグネチャを持たなければなりません。

    ```julia
    function diffusion((dx, x, u, t, args...; kwargs...)
        dx .= .... # dx を更新
    end
    ```

    さらに、`readout` は次のシグネチャを持たなければなりません。

    ```julia
    function readout(x, u, t)
        y = ...
        return y
    end
    ```


!!! warning
    新しい SDE システムは、正しく機能するために `AbstractSDESystem` のサブタイプでなければなりません。


# 例

```julia
julia> @def_sde_system mutable struct MySDESystem{DR, DF, RO, IP, OP} <: AbstractSDESystem
           η::Float64 = 1.
           drift::DR = (dx, x, u, t) -> (dx .= x)
           diffusion::DF = (dx, x, u, t, η=η) -> (dx .= η)
           readout::RO = (x, u, t) -> x 
           state::Vector{Float64} = rand(2) 
           input::IP = nothing 
           output::OP = Outport(2)
       end

julia> ds = MySDESystem();
```
