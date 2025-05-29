```
Overwrite(T, value::T) -> Construct{T}
Overwrite(T, getter) -> Construct{T}
Overwrite(subcon::Construct{T}, value::T) -> Construct{T}
Overwrite(subcon::Construct{T}, getter) -> Construct{T}
```

`getter`/`value` からシリアライズする際に値を上書きします。デシリアライズは単にそのまま渡します。

# 引数

  * `subcon::Construct{T}`: 基本となる構造体。
  * `value::T`: シリアライズ時に上書きする値。
  * `getter`: シリアライズ時に上書きする関数。関数は `(::T; contextkw...)` のようなシグネチャを持ち、冪等性を満たす必要があります（`getter(getter(x)) == getter(x)`）。

# 例

```jldoctest
julia> serialize(Overwrite(UInt8, 0x01), 2)
1-element Vector{UInt8}:
 0x01

julia> serialize(Overwrite(Int8, abs), -2)
1-element Vector{UInt8}:
 0x02

julia> deserialize(Overwrite(UInt8, 0x01), b"\x05")
0x05
```
