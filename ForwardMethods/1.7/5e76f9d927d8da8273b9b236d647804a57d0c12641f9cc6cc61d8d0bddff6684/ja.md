```
@forward_interface T [field=_field] [interface=name] [map=_map] [key=value...]
```

`interface`で定義されたメソッドを型`T`のオブジェクトに転送します。

# 引数

`name`は(:iteration, :indexing, :array, :vector, :dict, :lockable, :getfields, :setfields)のいずれかでなければならず、`name`の値`f`はインターフェース定義関数`$f_interface`に対応します（例：`array` => `array_interface`）。

`name`が`getfields`または`setfields`のいずれかである場合、`field`キーワード引数は無視されます。

それ以外の場合、`_field`は以下のいずれかの式でなければなりません。

  * `k::Symbol`または`k::QuoteNode`、または`getfield(_, k)`の形の式。この場合、メソッドは`getfield(x, k)`に転送されます。
  * `getproperty(_, k)`の形の式。この場合、メソッドは`getproperty(x, k)`に転送されます。
  * `t[args...]`の形の式。この場合、メソッドは`x[args...]`に転送されます。
  * または、単一引数関数`f`の形の式`f(_)`。この場合、メソッドは`f(x)`に転送されます。

# 追加引数

`key=value`のペアは、対応するインターフェース定義メソッドに転送されます。特に、`omit=func1`または`omit=[func1,func2, ..., funcn]`を指定すると、`func1`、...、`funcn`がこのマクロによって転送されるのを省略します。

[`@forward_methods`](@ref)も参照してください。
