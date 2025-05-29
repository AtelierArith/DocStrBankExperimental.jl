```
sim_dbm(tree::iTree; 
        x0  ::Float64 = 0.0,
        αx  ::Float64 = 0.0,
        σ20 ::Float64 = 0.1,
        ασ  ::Float64 = 0.0,
        γ   ::Float64 = 0.1,
        δt  ::Float64 = 1e-3)
```

初期値に基づいて拡散ブラウン運動をシミュレートします。
