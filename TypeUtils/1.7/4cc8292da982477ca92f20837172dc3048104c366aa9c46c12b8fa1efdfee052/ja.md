```
nearest(T::Type, x) -> y::T
```

は、`x` に最も近い型 `T` の値またはインスタンス `y` を返します。`T` が整数で `x` が実数の場合、これはクリッピングを伴う丸めとして見ることができます。
