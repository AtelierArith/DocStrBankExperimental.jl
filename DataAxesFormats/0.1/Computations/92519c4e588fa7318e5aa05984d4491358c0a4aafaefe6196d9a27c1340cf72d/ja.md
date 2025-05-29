[`@computation`](@ref)を使用する場合：

```
'''
...
# 契約
...
$(CONTRACT)
...
'''
@computation Contract(...) function something(daf::DafWriter, ...)
    return ...
end
```

この場合、`$(CONTRACT)`は[`Contract`](@ref)の説明で展開されます。これは`DocStringExtensions`に基づいています。

!!! note
    関数の最初の引数は[`DafWriter`](@ref)でなければならず、契約はこれに適用されます。

