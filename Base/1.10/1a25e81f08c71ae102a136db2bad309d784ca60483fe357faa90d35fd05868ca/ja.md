```
startswith(s::AbstractString, prefix::Regex)
```

`s`が正規表現パターン`prefix`で始まる場合は`true`を返します。

!!! note
    `startswith`はアンカーを正規表現にコンパイルせず、代わりにアンカーを`match_option`としてPCREに渡します。コンパイル時間が償却される場合、`occursin(r"^...", s)`は`startswith(s, r"...")`よりも速いです。


関連情報として[`occursin`](@ref)と[`endswith`](@ref)を参照してください。

!!! compat "Julia 1.2"
    このメソッドは少なくともJulia 1.2が必要です。


# 例

```jldoctest
julia> startswith("JuliaLang", r"Julia|Romeo")
true
```
