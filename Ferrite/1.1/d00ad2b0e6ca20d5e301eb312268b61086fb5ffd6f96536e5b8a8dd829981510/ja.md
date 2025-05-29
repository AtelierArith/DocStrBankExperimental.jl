```
add!(dh::DofHandler, name::Symbol, ip::Interpolation)
```

`ip`によって近似された`name`というフィールドをDofHandler `dh`に追加します。

フィールドは基盤となるグリッドのすべてのセルに追加されます。グリッドに複数のセルタイプが含まれている場合は[`SubDofHandler`](@ref)を使用するか、すべてのセルのサブセットにフィールドを追加します。
