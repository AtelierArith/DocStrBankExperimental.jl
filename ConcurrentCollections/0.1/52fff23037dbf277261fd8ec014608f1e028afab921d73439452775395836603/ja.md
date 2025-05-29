```
Keep(ans)
```

[`modify!`](@ref) で使用される特別な型で、スロットが変更されずに、いくつかの計算の結果 `ans` を呼び出し元に伝播させることを示します。

つまり、

```Julia
y = modify!(dict, key) do value
    Keep(f(something(value)))
end
y[]
```

は次の最適化です。

```Julia
r = Ref{Any}()
modify!(dict, key) do value
    r[] = f(something(value))
    Some(value)
end
r[]
```
