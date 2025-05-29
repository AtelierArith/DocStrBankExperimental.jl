```
ex = :(x * (m == n))
pat = :(_i == _j)
ex = without(ex, pat)  # ==> :x
```
