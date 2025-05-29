```
@def_dae_system ex
```

ここで `ex` は新しい AbstractDAESystem コンポーネントタイプを定義するための式です。使用法は次のとおりです：

```julia
@def_dae_system mutable struct MyDAESystem{T1,T2,T3,...,TN,OP,RH,RO,ST,IP,OP} <: AbstractDAESystem
    param1::T1 = param1_default                 # オプションフィールド 
    param2::T2 = param2_default                 # オプションフィールド 
    param3::T3 = param3_default                 # オプションフィールド
        ⋮
    paramN::TN = paramN_default                 # オプションフィールド 
    righthandside::RH = righthandside_function  # 必須フィールド
    readout::RO = readout_function              # 必須フィールド
    state::ST = state_default                   # 必須フィールド
    stateder::ST = stateder_default             # 必須フィールド
    diffvars::Vector{Bool} = diffvars_default   # 必須フィールド
    input::IP = input_default                   # 必須フィールド
    output::OP = output_default                 # 必須フィールド
end
```

ここで、`MyDAESystem` には `N` 個のパラメータがあります。`MyDAESystem` は `righthandside` と `readout` 関数によって表されます。`state`、`stateder`、`diffvars`、`input` および `output` は `MyDAESystem` の初期状態、微分変数の初期値、微分変数を示すベクトル、入力ポートおよび出力ポートです。

!!! warning
    `righthandside` は次のシグネチャを持たなければなりません 

    ```julia
    function righthandside(out, dx, x, u, t, args...; kwargs...)
        out .= .... # out を更新
    end
    ```

    また、`readout` は次のシグネチャを持たなければなりません 

    ```julia
    function readout(x, u, t)
        y = ...
        return y
    end
    ```


!!! warning
    新しい DAE システムは、正しく機能するために `AbstractDAESystem` のサブタイプでなければなりません。


# 例

```julia
julia> @def_dae_system mutable struct MyDAESystem{RH, RO, ST, IP, OP} <: AbstractDAESystem
        righthandside::RH = function sfuncdae(out, dx, x, u, t)
                out[1] = x[1] + 1 - dx[1]
                out[2] = (x[1] + 1) * x[2] + 2
            end 
        readout::RO = (x,u,t) -> x 
        state::ST = [1., -1]
        stateder::ST = [2., 0]
        diffvars::Vector{Bool} = [true, false]
        input::IP = nothing 
        output::OP = Outport(1)
        end

julia> ds = MyDAESystem();
```
