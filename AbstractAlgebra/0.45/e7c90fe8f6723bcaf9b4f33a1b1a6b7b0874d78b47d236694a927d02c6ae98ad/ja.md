```
gcdinv(f::T, g::T) where T <: RingElem
```

タプル `d, s` を返します。ここで、$d = gcd(f, g)$ であり、$s = (f/d)^{-1} \pmod{g/d}$ です。$d = 1$ であることは、$f$ が $g$ に対して可逆であることを意味し、その場合 $s = f^{-1} \pmod{g}$ となります。
