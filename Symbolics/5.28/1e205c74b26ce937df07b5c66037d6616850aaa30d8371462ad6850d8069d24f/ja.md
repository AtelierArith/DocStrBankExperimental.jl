```
@register_symbolic(expr, define_promotion = true, Ts = [Real])
```

適切なメソッドをオーバーロードして、Symbolicsが登録された関数に追跡するのを停止できるようにします。`define_promotion`がtrueの場合、次の形式のプロモーションメソッドが定義されます。

```julia
SymbolicUtils.promote_symtype(::typeof(f_registered), args...) = Real # または注釈付きの戻り値の型
```

1つの関数に対して複数の登録オーバーロードを定義する場合、最初のものを除いて、すべての他の登録は`define_promotion`を`false`に設定する必要があります。これはメソッドの上書きを避けるためです。

# 例

```julia
@register_symbolic foo(x, y)
@register_symbolic foo(x, y::Bool) false # 重複したプロモーションルールをオーバーロードしない
@register_symbolic goo(x, y::Int) # `y`はシンボリックオブジェクトを受け取るようにオーバーロードされていない
@register_symbolic hoo(x, y)::Int # `hoo`は`Int`を返す
```

配列を返す関数を登録するには、`@register_array_symbolic`を参照してください。
