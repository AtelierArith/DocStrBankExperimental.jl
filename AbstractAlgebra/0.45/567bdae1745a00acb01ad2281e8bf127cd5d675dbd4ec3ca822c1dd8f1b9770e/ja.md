```
gcd(a::FracElem{T}, b::FracElem{T}) where {T <: RingElem}
```

$$
a
$$

と$b$の最大公約数を返します。注意: $a/b$と$c/d$のGCDはgcd$(ad, bc)/bd$と定義され、最も簡単な形に還元されます。これには基底環の最大公約数関数の存在が必要です。
