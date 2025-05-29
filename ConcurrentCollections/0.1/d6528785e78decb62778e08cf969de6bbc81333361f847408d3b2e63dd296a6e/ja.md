```
Delete(ans)
```

[`modify!`](@ref) でスロットを削除することを示すために使用される特別な型です。

つまり、

```Julia
y = modify!(dict, key) do value
    Delete(f(something(value)))
end
y[]
```

は次の最適化です。

```Julia
r = Ref{Any}()
modify!(dict, key) do value
    r[] = f(something(value))
    nothing
end
r[]
```
