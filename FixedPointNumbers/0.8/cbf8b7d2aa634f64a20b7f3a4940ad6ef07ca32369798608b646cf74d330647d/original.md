```
sd, ad = scaledual(s::Number, a)
```

Return `sd` and `ad` such that `sd * ad == s * a`. When `a` is an array of FixedPoint numbers, `sd*ad` might be faster to compute than `s*a`.
