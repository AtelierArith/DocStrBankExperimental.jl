```
multiset(iter) -> MSet{eltype(iter)}
multiset(d::Dict{T, Int}) -> MSet{T}
multiset{l::Vector{T}, m::Vector{Int}} -> MSet{T}
```

次のいずれかを指定してください：

  * 有限イテレータ `iter`；
  * 値が正の整数である辞書 `d`；
  * リスト `l` と、`l` と同じ長さの正の整数のリスト `m`；

関連するマルチセット `M` を返します。

# 例

```jldoctest
julia> str = "A nice sentence"
"A nice sentence"

julia> multiset(str)
MSet{Char} with 15 elements:
  'n' : 3
  'A'
  'c' : 2
  'i'
  'e' : 4
  's'
  't'
  ' ' : 2

julia> multiset(Int[x^3%8 for x = 1:50])
MSet{Int64} with 50 elements:
  0 : 25
  5 : 6
  7 : 6
  3 : 6
  1 : 7

julia> d = Dict("a" => 4, "b" => 1, "c" =>9)
Dict{String, Int64} with 3 entries:
  "c" => 9
  "b" => 1
  "a" => 4

julia> multiset(d)
MSet{String} with 14 elements:
  "c" : 9
  "b"
  "a" : 4

julia> multiset(["a", "b", "c"], [4, 1, 9])
MSet{String} with 14 elements:
  "c" : 9
  "b"
  "a" : 4
```
