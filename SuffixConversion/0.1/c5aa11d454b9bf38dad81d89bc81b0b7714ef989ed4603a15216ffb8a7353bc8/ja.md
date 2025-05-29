```
@suffix T [= ....]
```

型 `T` のための [`SuffixConverter`](@ref) を定義します。同じ名前で、アンダースコアが接頭辞として付けられます。便利のために、`T` 自体を定義する式を受け取ることもできます。

# 例

既に定義された型を使用する

```julia
function addhalf(x::FT) where {FT}
    @suffix FT
    return x + 0.5_FT
end
```

型をインラインで定義する

```julia
function addhalf(x)
    @suffix FT = typeof(FT)
    return x + 0.5_FT
end
```
