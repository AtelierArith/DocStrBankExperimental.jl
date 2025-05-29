```
realnumtype(T::Type)
```

Tのサブタイプである`Real`の基になる数値型を返します。

Tの基になる`Real`型の間で型昇格を使用します。

例：

```julia

A = fill(fill(rand(Float32, 5), 10), 5)
realnumtype(typeof(A)) == Float32
```
