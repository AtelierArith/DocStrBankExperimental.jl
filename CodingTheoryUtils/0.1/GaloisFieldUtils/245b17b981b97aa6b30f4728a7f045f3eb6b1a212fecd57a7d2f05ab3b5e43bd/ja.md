```
bi2de(b::Vector{<:Integer})::Int
```

バイナリベクターを10進数に変換します。

# 引数

  * `b::Vector{<:Integer}`: バイナリ数を表す0と1のベクター

# 戻り値

  * `Int`: 入力バイナリベクターの10進数表現

# 例

```julia
julia> bi2de([1, 0, 1])
5

julia> bi2de([0, 1, 0, 1])
10
```
