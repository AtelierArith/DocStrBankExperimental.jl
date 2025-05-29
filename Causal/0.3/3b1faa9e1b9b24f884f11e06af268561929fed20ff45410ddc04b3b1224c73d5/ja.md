```
@def_static_system ex
```

ここで `ex` は新しい AbstractStaticSystem コンポーネントタイプを定義するための式です。使用法は次のとおりです：

```julia
@def_source struct MyStaticSystem{T1,T2,T3,...,TN,OP, RO} <: AbstractStaticSystem
    param1::T1 = param1_default     # オプションフィールド 
    param2::T2 = param2_default     # オプションフィールド 
    param3::T3 = param3_default     # オプションフィールド
        ⋮
    paramN::TN = paramN_default     # オプションフィールド 
    input::IP = input_default       # 必須フィールド
    output::OP = output_default     # 必須フィールド 
    readout::RO = readout_function  # 必須フィールド
end
```

ここで、`MyStaticSystem` は `N` 個のパラメータ、`output` ポート、`input` ポート、および `readout` 関数を持っています。

!!! warning
    `input`、`output` および `readout` は新しい静的システムを定義するための必須フィールドです。残りのフィールドはシステムのパラメータです。


!!! warning
    `readout` は二引数の関数でなければなりません。すなわち、時間 `t` と入力値 `u` の関数です。


!!! warning
    新しい静的システムは正しく機能するために `AbstractStaticSystem` のサブタイプでなければなりません。


# 例

```julia
julia> @def_static_system struct MyStaticSystem{IP, OP, RO} <: AbstractStaticSystem 
       α::Float64 = 1. 
       β::Float64 = 2. 
       input::IP = Inport() 
       output::OP = Outport() 
       readout::RO = (t,u) -> α * u[1] + β * u[2]
       end

julia> sys = MyStaticSystem(); 

julia> sys.α
1.0

julia> sys.input
1-element Inport{Inpin{Float64}}:
 Inpin(eltype:Float64, isbound:false)
```
