```
complex(T::Type)
```

値の型 `T` を複素数として表すことができる適切な型を返します。`typeof(complex(zero(T)))` と同等です。

# 例

```jldoctest
julia> complex(Complex{Int})
Complex{Int64}

julia> complex(Int)
Complex{Int64}
```
