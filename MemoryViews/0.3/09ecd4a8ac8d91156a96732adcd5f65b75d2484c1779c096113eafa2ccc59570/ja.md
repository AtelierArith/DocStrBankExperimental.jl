```
MemoryKind
```

トレイトオブジェクトは、型の値が自分自身の `MemoryView` と意味的に等しいかどうかを示すために使用されます。もしそうであれば、`MemoryKind(T)` は `IsMemory` のインスタンスを返すべきであり、そうでなければ `NotMemory()` を返します。デフォルトの実装 `MemoryKind(::Type)` は `NotMemory()` を返します。

もし `MemoryKind(T) isa IsMemory{M}` であれば、次のことが成り立たなければなりません：

1. `M` は `MemoryView` の具体的なサブタイプです。`m::IsMemory{M}` から `M` を取得するには、`inner(m)` を使用します。
2. `MemoryView(T)` は `M` の有効なインスタンスです。
3. すべてのインスタンス `x::T` に対して `MemoryView(x) == x` です。

一部のオブジェクトは `IsMemory` でなくても `MemoryView` に変換できます。例えば、`MemoryView(::String)` は有効な `MemoryView` を返しますが、`MemoryKind(String) === NotMemory()` です。これは、文字列がメモリビューとは異なる意味を持つためです - 後者は密な `AbstractArray` ですが、文字列はそうではなく、したがって4番目の要件 `MemoryView(x::String) == x` は成り立ちません。

参照： [`MemoryView`](@ref)
