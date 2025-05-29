rewrite(ex, pat, rpat)

Rewrite expression `ex` according to a transform from pattern `pat` to a substituting expression `rpat`. Example (derivative of x^n):

```
ex = :(u ^ v)
pat = :(_x ^ _n)
rpat = :(_n * _x ^ (_n - 1))
rewrite(ex, pat, rpat) # ==> :(v * u ^ (v - 1))
```
