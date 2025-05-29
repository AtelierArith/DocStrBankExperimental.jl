```
static_promote(x::AbstractRange{<:Integer}, y::AbstractRange{<:Integer})
```

静的パラメータを保持する新しい範囲に2つの等しい範囲を結合するための型安定なメソッドです。`x != y` の場合はエラーをスローします。

# 例

```julia
julia> static_promote(static(1):10, 1:static(10))
static(1):static(10)

julia> static_promote(1:2:9, static(1):static(2):static(9))
static(1):static(2):static(9)
```
