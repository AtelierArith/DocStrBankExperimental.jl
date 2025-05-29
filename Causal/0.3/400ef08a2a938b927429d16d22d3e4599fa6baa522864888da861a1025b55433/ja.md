```
@def_source ex
```

ここで `ex` は新しい AbstractSource コンポーネントタイプを定義するための式です。使用法は次のとおりです：

```julia
@def_source struct MySource{T1,T2,T3,...,TN,OP, RO} <: AbstractSource
    param1::T1 = param1_default     # オプションフィールド 
    param2::T2 = param2_default     # オプションフィールド 
    param3::T3 = param3_default     # オプションフィールド
        ⋮
    paramN::TN = paramN_default     # オプションフィールド 
    output::OP = output_default     # 必須フィールド 
    readout::RO = readout_function  # 必須フィールド
end
```

ここで、`MySource` は `N` 個のパラメータ、`output` ポート、および `readout` 関数を持っています。

!!! warning
    `output` と `readout` は新しいソースを定義するための必須フィールドです。残りのフィールドはソースのパラメータです。


!!! warning
    `readout` は単一引数の関数でなければなりません。すなわち、時間 `t` の関数です。


!!! warning
    新しいソースは正しく機能するために `AbstractSource` のサブタイプでなければなりません。


# 例

```julia
julia> @def_source struct MySource{OP, RO} <: AbstractSource
       a::Int = 1 
       b::Float64 = 2. 
       output::OP = Outport() 
       readout::RO = t -> (a + b) * sin(t)
       end

julia> gen = MySource();

julia> gen.a 
1

julia> gen.output
1-element Outport{Outpin{Float64}}:
 Outpin(eltype:Float64, isbound:false)
```
