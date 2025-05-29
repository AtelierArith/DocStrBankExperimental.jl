```
flux_central(u_ll, u_rr, orientation_or_normal_direction, equations::AbstractEquations)
```

古典的な中央数値フラックス `f((u_ll) + f(u_rr)) / 2`。このフラックスが体積フラックスとして使用されると、離散化は古典的な弱形式DG法と同等です（浮動小数点誤差を除く）。
