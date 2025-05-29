```
radical_extension(n::Int, a::NumFieldElem, s = "_$";
               check = true, cached = true) -> NumField, NumFieldElem
```

数体 $K$ の要素 $a$ と整数 $n$ が与えられたとき、定義多項式 $x^n - a$ を持つ $K$ の単純拡張を作成します。

# 例

```jldoctest
julia> radical_extension(5, QQ(2), "a")
(Number field of degree 5 over QQ, a)
```
