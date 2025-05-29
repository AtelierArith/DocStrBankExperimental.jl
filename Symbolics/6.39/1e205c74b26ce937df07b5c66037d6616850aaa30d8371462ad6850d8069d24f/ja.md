```
@register_symbolic(expr, define_promotion = true, Ts = [Real])
```

適切なメソッドをオーバーロードして、Symbolicsが登録された関数にトレースするのを停止できるようにします。`define_promotion`がtrueの場合、次の形式のプロモーションメソッドが定義されます。

```julia
SymbolicUtils.promote_symtype(::typeof(f_registered), args...) = Real # または注釈付きの戻り値の型
```

1つの関数に対して複数の登録オーバーロードを定義する際は、最初のものを除いて、他のすべての登録で`define_promotion`を`false`に設定して、メソッドの上書きを避ける必要があります。

# 例

```julia
@register_symbolic foo(x, y)
@register_symbolic foo(x, y::Bool) false # 重複したプロモーションルールをオーバーロードしない
@register_symbolic goo(x, y::Int) # `y`はシンボリックオブジェクトを受け取るようにオーバーロードされていない
@register_symbolic hoo(x, y)::Int # `hoo`は`Int`を返す
```

配列を返す関数を登録するには、`@register_array_symbolic`を参照してください。
