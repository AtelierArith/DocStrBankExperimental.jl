```
gcd(a::RationalFunctionFieldElem{T, U}, b::RationalFunctionFieldElem{T, U}) where {T <: FieldElement, U <: Union{PolyRingElem, MPolyRingElem}}
```

$ a $ と $ b $ の最大公約数を返します。注意: $ a/b $ と $ c/d $ の GCD を gcd$(ad, bc)/bd$ と定義し、最も簡単な形にします。
