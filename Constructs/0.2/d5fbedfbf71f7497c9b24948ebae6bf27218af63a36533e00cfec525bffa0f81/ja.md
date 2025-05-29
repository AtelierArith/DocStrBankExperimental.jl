```
Try(T1|subcon1, T2|subcon2, ...) -> Construct{Union{T1, T2, ...}}
Try{TU}(T1|subcon1, T2|subcon2, ...) -> Construct{TU}
```

各 `subcon` を試し、最初に成功したものを使用します。

# 例

別の非網羅的な列挙型：

```jldoctest
julia> @enum Fruit::UInt8 apple=1 banana=2 orange=3

julia> deserialize(Try(Fruit, UInt8), b"\x02")
banana::Fruit = 0x02

julia> deserialize(Try(Fruit, UInt8), b"\x04")
0x04
```
