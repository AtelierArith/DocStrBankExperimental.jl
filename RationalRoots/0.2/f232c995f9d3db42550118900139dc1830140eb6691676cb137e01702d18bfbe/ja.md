```
signedroot([R<:RationalRoot,] x)
```

返す `sign(x)*sqrt(abs(x)) == x/sqrt(abs(x))`。最初の引数がない場合、この値は `x isa AbstractFloat` の場合は浮動小数点数として、`x isa Union{Integer,Rational}` の場合は `RationalRoot` として与えられます。最初の引数がある場合、返り値の型は `RationalRoot` または特定の `RationalRoot{T}` と指定され、浮動小数点数 `x` の場合、結果は最初に `Base.rationalize{T}` によって有理化されます。

# 例

```jldoctest
julia> signedroot(3)
+√(3//1)

julia> signedroot(-4.0)
-2.0

julia> signedroot(RationalRoot, 5.2)
+√(26//5)

julia> signedroot(RationalRoot{Int8}, 8)
+√(8//1)
```
