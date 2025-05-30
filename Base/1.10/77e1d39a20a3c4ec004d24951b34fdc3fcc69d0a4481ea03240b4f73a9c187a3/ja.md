```
startswith(s::AbstractString, prefix::AbstractString)
```

`s`が`prefix`で始まる場合は`true`を返します。`prefix`が文字のベクターまたはセットである場合、`s`の最初の文字がそのセットに属するかどうかをテストします。

他にも[`endswith`](@ref)、[`contains`](@ref)を参照してください。

# 例

```jldoctest
julia> startswith("JuliaLang", "Julia")
true
```
