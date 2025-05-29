```
substatic"string"[N]
```

「string」から [`SubStaticString`](@ref) を作成します。オプションで、コードユニットの数 `N` を指定できます。結果は `SubStaticString{N}` になりますが、使用されるコードユニットは元の文字列のものになります。

# 例

```jldoctest
julia> substatic"Як ти?"
substatic"Як ти?"10

julia> substatic"Як ти?"256
substatic"Як ти?"256
```
