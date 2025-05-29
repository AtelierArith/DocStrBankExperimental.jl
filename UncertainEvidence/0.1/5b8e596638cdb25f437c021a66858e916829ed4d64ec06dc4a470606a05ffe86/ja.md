```
bpa(X...)
```

ペアの質量割り当て `X` から正規化された基本確率割り当て (BPA) 構造を作成します。

# 例

```juliadoctest
julia> A = bpa(Set("a") => 0.1, Set("b") => 0.2)
Dict{Set{Char}, Float64} with 3 entries:
    Set(['a'])      => 0.1
    Set(['b'])      => 0.2
    Set(['a', 'b']) => 0.7
```

参照: [`BPA`](@ref). ```
