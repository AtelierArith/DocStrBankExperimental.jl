```
add_anis(sim::AbstractSim, Ku::NumberOrArrayOrFunction; axis=(0,0,1), name="anis")
```

システムに異方性を追加します。エネルギー密度は次のように与えられます。

$$
    E_\mathrm{anis} =  K_{u} (1 - \vec{m} \cdot \hat{u})^2
$$
