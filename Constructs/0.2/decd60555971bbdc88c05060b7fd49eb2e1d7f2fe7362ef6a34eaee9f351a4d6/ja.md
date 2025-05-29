```
PrimitiveIO(T) -> Construct{T}
```

`read`（[`read`](https://docs.julialang.org/en/v1.6/base/io-network/#Base.read)）と`write`（[`write`](https://docs.julialang.org/en/v1.6/base/io-network/#Base.write)）に基づいて、`type`のためのプリミティブIO構造体を定義します。

これは`Bool`、`Char`、`UInt8`、`UInt16`、`UInt32`、`UInt64`、`UInt128`、`Int8`、`Int16`、`Int32`、`Int64`、`Int128`、`Float16`、`Float32`、および`Float64`のデフォルト構造体です。

# 例

```jldoctest
julia> serialize(PrimitiveIO(Complex{Bool}), im)
2-element Vector{UInt8}:
 0x00
 0x01
```
