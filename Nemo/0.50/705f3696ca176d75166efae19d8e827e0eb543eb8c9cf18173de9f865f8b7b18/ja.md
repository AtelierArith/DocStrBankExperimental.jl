```
  simplest_between(l::QQFieldElem, r::QQFieldElem)
```

閉区間 $[l, r]$ 内の最も単純な分数を返します。標準的な分数 $a_1 / b_1$ は、$a_2 / b_2$ よりも単純であると定義されるのは、$b_1 < b_2$ であるか、または $b_1 = b_2$ かつ $a_1 < a_2$ の場合のみです。

# 例

```jldoctest
julia> simplest_between(QQ(1//10), QQ(3//10))
1//4
```
