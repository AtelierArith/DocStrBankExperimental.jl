```
point_ordering!(B::BracketAlgebra, point_ordering::AbstractVector{<:Integer}=collect(1:B.n))
```

ブラケット代数 `B` のポイント順序を `point_ordering` に更新し、更新されたブラケット代数を返します。

警告: ポイント順序を変更しても、すでに生成された `B` の要素の表現は変更されず、これらの要素を扱う際に誤った結果を引き起こす可能性があります。望ましいポイント順序で新しいブラケット代数を作成することをお勧めします。

# 例

```jldoctest
julia> point_ordering!(BracketAlgebra(6,3), [6,5,4,3,2,1])
Bracket algebra over P^3 on 6 points with point ordering 6 < 5 < 4 < 3 < 2 < 1 and coefficient ring Integers.
```
