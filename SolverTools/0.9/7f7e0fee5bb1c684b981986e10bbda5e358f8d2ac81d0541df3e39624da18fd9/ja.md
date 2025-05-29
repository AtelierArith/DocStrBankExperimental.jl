```
slope, qs = compute_Hs_slope_qs!(Hs, H, s, g)
```

計算します

```
Hs = H * s
slope = dot(g,s)
qs = ¹/₂sᵀHs + slope
```
