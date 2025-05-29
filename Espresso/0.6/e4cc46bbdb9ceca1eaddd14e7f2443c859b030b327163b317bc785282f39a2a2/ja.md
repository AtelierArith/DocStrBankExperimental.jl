rewrite(ex, pat, rpat)

式 `ex` をパターン `pat` から置換式 `rpat` に従って書き換えます。例（x^n の導関数）：

```
ex = :(u ^ v)
pat = :(_x ^ _n)
rpat = :(_n * _x ^ (_n - 1))
rewrite(ex, pat, rpat) # ==> :(v * u ^ (v - 1))
```
