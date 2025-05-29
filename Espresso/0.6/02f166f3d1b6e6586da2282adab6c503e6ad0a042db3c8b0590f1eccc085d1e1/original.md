Find sub-expressions matching a pattern. Example:

```
ex = :(a * f(x) + b * f(y))
pat = :(f(_))
findex(pat, ex)   # ==> [:(f(x)), :(f(y))]
```
