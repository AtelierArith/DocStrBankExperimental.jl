```
specificweight(h::Real=0,W::Weather=Standard) = density(h,W)*gravity(h,W)
```

特定重量は、`Weather` の位置の高度 `h` での値（kg⋅m⁻²⋅s⁻² または slugs⋅ft⁻²⋅s⁻²）です。
