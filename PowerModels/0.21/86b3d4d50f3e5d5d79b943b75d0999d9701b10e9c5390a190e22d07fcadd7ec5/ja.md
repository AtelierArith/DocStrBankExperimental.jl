複素変換比の変数を持つオーム制約を作成します（yの接尾辞はYが直交形式であることを示します）

```
p[t_idx] ==  (g+g_to)*v[t_bus]^2 + (-g)/tm*(v[t_bus]*v[f_bus]*cos(t[t_bus]-t[f_bus]+ta)) + (-b)/tm*(v[t_bus]*v[f_bus]*sin(t[t_bus]-t[f_bus]+ta))
q[t_idx] == -(b+b_to)*v[t_bus]^2 - (-b)/tm*(v[t_bus]*v[f_bus]*cos(t[f_bus]-t[t_bus]+ta)) + (-g)/tm*(v[t_bus]*v[f_bus]*sin(t[t_bus]-t[f_bus]+ta))
```
