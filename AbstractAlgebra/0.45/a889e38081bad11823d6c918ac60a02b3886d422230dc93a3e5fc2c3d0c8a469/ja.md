```
gcdx(f::T, g::T) where T <: RingElem
```

三つ組 `d, s, t` を返します。ここで $d = gcd(f, g)$ であり、$d = sf + tg$ です。$s$ は $g/d$ に対して緩やかに約分され、$t$ は $f/d$ に対して緩やかに約分されています。
