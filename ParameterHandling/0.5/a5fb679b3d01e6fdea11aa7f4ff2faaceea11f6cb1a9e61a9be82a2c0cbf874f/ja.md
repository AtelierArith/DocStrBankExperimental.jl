```
positive(x::Array{<:Real})
```

おおよそ `map(positive, x)` と同等ですが、アルゴリズミック微分（特に Zygote を使用）を通じて効率的に微分できるように実装されています。
