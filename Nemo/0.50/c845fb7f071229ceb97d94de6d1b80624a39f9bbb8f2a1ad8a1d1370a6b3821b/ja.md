```
  simplest_rational_inside(x::ArbFieldElem)
```

ボール $x$ の中にある最も単純な分数を返します。標準的な分数 $a_1/b_1$ は、$b_1 < b_2$ または $b_1 = b_2$ かつ $a_1 < a_2$ の場合に、$a_2/b_2$ よりも単純であると定義されます。

# 例

```jldoctest
julia> RR = ArbField(64)
精度64ビットおよび誤差範囲を持つ実数フィールド

julia> simplest_rational_inside(const_pi(RR))
8717442233//2774848045
```
