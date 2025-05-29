```
@def_sink ex
```

ここで `ex` は新しい AbstractSink コンポーネントタイプを定義するための式です。使用法は次のとおりです：

```julia
@def_sink struct MySink{T1,T2,T3,...,TN, A} <: AbstractSink
    param1::T1 = param1_default     # オプションフィールド 
    param2::T2 = param2_default     # オプションフィールド 
    param3::T3 = param3_default     # オプションフィールド
        ⋮
    paramN::TN = paramN_default     # オプションフィールド 
    action::A = action_function     # 必須フィールド
end
```

ここで、`MySink` は `N` パラメータと `action` 関数を持っています。

!!! warning `action` 関数は `action(sink::MySink, t, u)` というメソッドを持っている必要があります。ここで `t` は時間データで、`u` はシンクに流れ込むデータです。

!!! warning 新しい静的システムは正しく機能するために `AbstractSink` のサブタイプである必要があります。

# 例

```julia
julia> @def_sink struct MySink{A} <: AbstractSink 
       action::A = actionfunc
       end

julia> actionfunc(sink::MySink, t, u) = println(t, u)
actionfunc (generic function with 1 method)

julia> sink = MySink();

julia> sink.action(sink, ones(2), ones(2) * 2)
[1.0, 1.0][2.0, 2.0]
```
