```
DissipationLocalLaxFriedrichs(max_abs_speed=max_abs_speed_naive)
```

ローカルLax-Friedrichs消散オペレーターを作成します。最大絶対波速度は `max_abs_speed(u_ll, u_rr, orientation_or_normal_direction, equations)` として推定され、デフォルトは [`max_abs_speed_naive`](@ref) です。
