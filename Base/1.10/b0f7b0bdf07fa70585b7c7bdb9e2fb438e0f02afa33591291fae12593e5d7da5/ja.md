```
@lock l expr
```

`lock(f, l::AbstractLock)`のマクロ版ですが、`f`関数の代わりに`expr`を使用します。次のように展開されます：

```julia
lock(l)
try
    expr
finally
    unlock(l)
end
```

これは、`do`ブロックを使用した[`lock`](@ref)と似ていますが、クロージャを作成することを避けるため、パフォーマンスを向上させることができます。
