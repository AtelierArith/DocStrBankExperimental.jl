```
bounded(val::Array{<:Real}, lower_bound::Real, upper_bound::Real)
```

おおよそ `bounded.(val, lower_bound, upper_bound)` と同等ですが、非平坦化が効率的に微分できるようにアルゴリズム的微分（特にZygote）を使用して実装されています。
