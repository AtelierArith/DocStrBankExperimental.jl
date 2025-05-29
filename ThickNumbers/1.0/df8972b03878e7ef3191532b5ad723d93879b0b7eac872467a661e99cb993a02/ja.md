```
isapprox_tn(a::ThickNumber, b::ThickNumber; atol=0, rtol::Real=atol>0 ? 0 : √eps)
a ⩪ b (`\dotsim`-TAB)
```

`a` と `b` が両方空であるか、または両方が `loval` と `hival` がほぼ等しい (≈) 場合に `true` を返します。それ以外の場合は `false` です。
