```
intensity(h::Real=0,W::Weather=Standard) = intensity(W(h))
```

位置における`Weather`の高度`h`での瞬時強度`I`（W⋅m⁻²またはslug⋅s⁻³）。
