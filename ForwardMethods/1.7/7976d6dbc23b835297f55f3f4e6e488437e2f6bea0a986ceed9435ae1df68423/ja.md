```
@define_interface T [interface=name] [kwargs...]
```

型 `T` のオブジェクトのための `interface` を定義します。

# 引数

`name` は (:properties, :equality, :setfields, :getfields) のいずれかでなければならず、`name` の値 `f` はインターフェース定義関数 `$f_interface` に対応します（例：`array` => `array_interface`）。

`key=value` のペアは、対応するインターフェース定義メソッドに転送されます。特に、`omit=func1` または `omit=[func1,func2, ..., funcn]` を指定すると、`func1` から `funcn` までがこのマクロによって転送されるのを省略します。

特定のキーワード引数が必要な場合は、各 :name_interface のドキュメントを参照してください。
