```
readcsv2(source, T::Type=Any; opts...)
```

`readdlm2()`と同等で、区切り文字は `','`、小数点は `'.'` です。デフォルトの型 `Any` は、`Bool`、`Int`、`Float64`、`Complex`、`Rational`、`Missing`、`DateTime`、`Date`、および `Time` の解析を有効にします。

# コード例

```jldoctest
julia> using ReadWriteDlm2

julia> B = Any[1 complex(1.5,2.7);1.0 1//3];

julia> writecsv2("test.csv", B)

julia> readcsv2("test.csv")
2×2 Array{Any,2}:
 1    1.5+2.7im
 1.0    1//3
```
