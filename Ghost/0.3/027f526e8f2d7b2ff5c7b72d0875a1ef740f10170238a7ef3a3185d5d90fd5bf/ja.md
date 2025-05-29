```
trace(f, args...; is_primitive, primitives)
```

関数呼び出しをトレースし、呼び出し値とテープを生成します。

`trace`はテープにプリミティブメソッドを記録し、非プリミティブに再帰的に潜ります。特定のメソッドがプリミティブであることを`trace`に伝える方法は2つあります：

  * `is_primitive(sig) -> Bool`関数を提供する。ここで`sig`はメソッドシグネチャであり、例えば`Tuple{map(typeof, (f, args...))...}`です。
  * イテラブルな`primitives`を提供する。この場合、`trace`はこの関数のすべてのメソッドと一致します。
