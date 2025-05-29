Remove rpatpression conforming to a pattern. Example:

```
ex = :(x * (m == n))
pat = :(_i == _j)
ex = without(ex, pat)  # ==> :x
```
