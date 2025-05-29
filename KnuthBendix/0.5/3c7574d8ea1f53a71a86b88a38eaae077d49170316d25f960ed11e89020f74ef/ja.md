```
Alphabet(letters::AbstractVector[, inversions])
```

アルファベットは、共通の型 `T` の記号で構成されています。

`Alphabet` は、連続する整数とその文字との間の双射を定義します。つまり、文字のインデックスを照会したり、与えられたインデックスに対応する文字を取得したりできます。

# 例

```jldoctest
julia> al = Alphabet([:a, :b, :c])
Alphabet of Symbol
  1. a
  2. b
  3. c

julia> al[2]
:b

julia> al[:c]
3

julia> Alphabet([:a, :A, :b], [2, 1, 0])
Alphabet of Symbol
  1. a    (inverse of: A)
  2. A    (inverse of: a)
  3. b
```
