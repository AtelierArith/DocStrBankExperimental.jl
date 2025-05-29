```
FORTRAN_eltype_char(T::Type)
```

FORTRAN datatype description character for julia type `T`: 

Bool => 'L', UInt8 => 'B', Int16 => 'I', UInt16 => 'I', Int32 => 'J',  UInt32 => 'J', Int64 => 'K', UInt64 => 'K', Float32 => 'E', Float64 => 'D',  ComplexF32 => 'C', ComplexF64 => 'M'

The character '-' is returned for non-primitive FORTRAN datatypes and for  primitive datatypes not included in the FITS standard.

#### Examples:

```
julia> T = Type[Bool, Int8, UInt8, Int16, UInt16, Int32, UInt32, Int64, UInt64];

julia> print([FORTRAN_eltype_char(T[i]) for i ∈ eachindex(T)])
Int8: datatype not part of the FITS standard
['L', '-', 'B', 'I', 'I', 'J', 'J', 'K', 'K']

julia> T = [Float16, Float32, Float64, ComplexF32, ComplexF64];

julia> print([FORTRAN_eltype_char(T[i]) for i ∈ eachindex(T)])
Float16: datatype not part of the FITS standard
['-', 'E', 'D', 'C', 'M']

julia> T = [String, Vector{Char}, FITS];

julia> print([FORTRAN_eltype_char(T[i]) for i ∈ eachindex(T)])
Vector{Char}: not a FORTRAN datatype
FITS: not a FORTRAN datatype
['A', 'A', '-', '-']
```
