ACモデルのオーム制約を作成します（yの後の接尾辞はY値が直交形式であることを示します）

```
p[t_idx] ==  (g+g_to)*v[t_bus]^2 + -g*v[t_bus]*v[f_bus]/tr*cos(t[t_bus]-t[f_bus]+as) + -b*v[t_bus]*v[f_bus]/tr*sin(t[t_bus]-t[f_bus]+as)
q[t_idx] == -(b+b_to)*v[t_bus]^2 +  b*v[t_bus]*v[f_bus]/tr*cos(t[f_bus]-t[t_bus]+as) + -g*v[t_bus]*v[f_bus]/tr*sin(t[t_bus]-t[f_bus]+as)
```
