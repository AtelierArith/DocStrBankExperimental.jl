与えられたスタビライザーからパウリ演算子を生成します。

**スタビライザーがすでに標準形であることを前提としています。** パウリ演算子をその場で修正し、位相まで逆に生成します。その位相は修正された演算子に残され、位相まで単位元であるべきです。新しい演算子と、生成に使用された `stabilizer` の要素を示すインデックスのリストを返します。

```jldoctest
julia> ghz = S"XXXX
               ZZII
               IZZI
               IIZZ";


julia> canonicalize!(ghz)
+ XXXX
+ Z__Z
+ _Z_Z
+ __ZZ

julia> generate!(P"-ZIZI", ghz)
(- ____, [2, 4])
```

パウリ演算子が与えられた表から生成できない場合、`nothing` が返されます。

```jldoctest
julia> generate!(P"XII",canonicalize!(S"ZII")) === nothing
true

julia> generate!(P"XII",canonicalize!(S"XII")) === nothing
false
```
