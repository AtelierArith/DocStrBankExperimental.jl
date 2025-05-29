```
NGramIterator(s, n=3, b=256, m=typemax(Int))
```

[`NGramIterator`](@ref)を構築します。`s`が`AbstractString`の場合、最初に`Base.codeunits`を使用して整数に変換されます。

# 例

```jldoctest
julia> NGramIterator("deadbeef", 3, 256, 17) |> collect
10-element Vector{Int64}:
  2
 16
  9
  9
  6
 10
 11
 15
  2
  6

julia> NGramIterator(collect(1:9), 3, 10, 1009) |> collect
11-element Vector{Int64}:
 221
 212
 123
 234
 345
 456
 567
 678
 789
 893
 933

julia> Mill.string_start_code()
0x02

julia> Mill.string_end_code()
0x03
```

関連情報: [`NGramMatrix`](@ref), [`ngrams`](@ref), [`ngrams!`](@ref), [`countngrams`](@ref),     [`countngrams!`](@ref).
