```
endswith(s::AbstractString, suffix::AbstractString)
```

`s`が`suffix`で終わる場合は`true`を返します。`suffix`が文字のベクターまたはセットである場合、`s`の最後の文字がそのセットに属するかどうかをテストします。

関連情報として[`startswith`](@ref)、[`contains`](@ref)を参照してください。

# 例

```jldoctest
julia> endswith("Sunday", "day")
true
```
