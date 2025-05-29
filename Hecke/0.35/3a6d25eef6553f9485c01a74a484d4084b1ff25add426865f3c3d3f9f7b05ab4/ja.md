```
(-)(s::MSet, itrs...) -> MSet
```

集合 `s` の補集合に関連するマルチセットを、`itrs` のコレクションから返します。

`setdiff(s, itrs...)` のエイリアスです。

# 例

```jldoctest
julia> m = multiset("A very nice sentence")
MSet{Char} with 20 elements:
  'n' : 3
  'e' : 5
  'A'
  'y'
  'i'
  'r'
  's'
  't'
  ' ' : 3
  'c' : 2
  'v'

julia> n = multiset("A nice sentence")
MSet{Char} with 15 elements:
  'n' : 3
  'A'
  'c' : 2
  'i'
  'e' : 4
  's'
  't'
  ' ' : 2

julia> n-m
MSet{Char}()

julia> m-n
MSet{Char} with 5 elements:
  'e'
  'y'
  'r'
  ' '
  'v'
```
