```
Const([T|subcon], value::T) -> Construct{T}
```

定数 `value` を定義します。通常、ファイルヘッダーに使用されます。

# 引数

  * `subcon::Construct{T}`: 基本となる構造体。
  * `value::T`: 期待される値。

# 例

```jldoctest
julia> serialize(Const(0x01), 0x01)
1-element Vector{UInt8}:
 0x01

julia> deserialize(Const(0x01), b"\x01")
0x01
```

```jldoctest
julia> serialize(Const(0x01), 0x03)
ERROR: ValidationError: 3 mismatch the const value 1.
[...]

julia> deserialize(Const(0x01), b"\x02")
ERROR: ValidationError: 2 mismatch the const value 1.
[...]
```
