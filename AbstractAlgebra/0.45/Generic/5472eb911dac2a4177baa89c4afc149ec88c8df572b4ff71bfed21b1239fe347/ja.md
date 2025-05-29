```
isless(p::FreeAssociativeAlgebraElem{T}, q::FreeAssociativeAlgebraElem{T}) where T
```

項に対する次数辞書順の順序付けを実装します。つまり、まず最大単項の次数が比較され、同じ場合は辞書順で比較され、さらに同じ場合は係数が比較されます。すべてがまだ同じ場合は、次に大きい単項が比較され、最後に単項の数が比較されます。係数も比較されるため、これは係数環がislessを実装している場合にのみ機能します。

文字の順序は、代数を初期化する際に与えられた順序の逆です。

# 例

```jldoctest
julia> R, (x, y) = free_associative_algebra(QQ, ["x", "y"]);

julia> x < y^2
true

julia> x^2 < x^2 + y
true

julia> y < x
true

julia> x^2 < 2*x^2
true
```
