```
FORTRAN_eltype_char(T::Type)
```

FORTRAN データ型の説明文字は、julia 型 `T` に対して次のようになります：

Bool => 'L', UInt8 => 'B', Int16 => 'I', UInt16 => 'I', Int32 => 'J',  UInt32 => 'J', Int64 => 'K', UInt64 => 'K', Float32 => 'E', Float64 => 'D',  ComplexF32 => 'C', ComplexF64 => 'M'

非プリミティブ FORTRAN データ型および FITS 標準に含まれていないプリミティブデータ型には、文字 '-' が返されます。

#### 例:

```
julia> T = Type[Bool, Int8, UInt8, Int16, UInt16, Int32, UInt32, Int64, UInt64];

julia> print([FORTRAN_eltype_char(T[i]) for i ∈ eachindex(T)])
Int8: FITS 標準の一部ではないデータ型
['L', '-', 'B', 'I', 'I', 'J', 'J', 'K', 'K']

julia> T = [Float16, Float32, Float64, ComplexF32, ComplexF64];

julia> print([FORTRAN_eltype_char(T[i]) for i ∈ eachindex(T)])
Float16: FITS 標準の一部ではないデータ型
['-', 'E', 'D', 'C', 'M']

julia> T = [String, Vector{Char}, FITS];

julia> print([FORTRAN_eltype_char(T[i]) for i ∈ eachindex(T)])
Vector{Char}: FORTRAN データ型ではない
FITS: FORTRAN データ型ではない
['A', 'A', '-', '-']
```
