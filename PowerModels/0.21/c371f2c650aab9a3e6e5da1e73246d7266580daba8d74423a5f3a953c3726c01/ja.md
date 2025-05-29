複素変換比の変数を持つオーム制約を作成します（yの接尾辞はYが直交形式であることを示します）

```
p[f_idx] ==  (g+g_fr)/tm*v[f_bus]^2 + (-g)/tm*(v[f_bus]*v[t_bus]*cos(t[f_bus]-t[t_bus]-ta)) + (-b)/tm*(v[f_bus]*v[t_bus]*sin(t[f_bus]-t[t_bus]-ta))
q[f_idx] == -(b+b_fr)/tm*v[f_bus]^2 - (-b)/tm*(v[f_bus]*v[t_bus]*cos(t[f_bus]-t[t_bus]-ta)) + (-g)/tm*(v[f_bus]*v[t_bus]*sin(t[f_bus]-t[t_bus]-ta))
```
