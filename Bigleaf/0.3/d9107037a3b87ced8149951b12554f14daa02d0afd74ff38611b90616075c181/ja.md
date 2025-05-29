```
ms_to_mol(G_ms,Tair,pressure; constants=BigleafConstants())
mol_to_ms(G_mol,Tair,pressure; constants=BigleafConstants())
```

質量 (m s-1) からモル単位 (mol m-2 s-1) への導電率の変換、またはその逆

# 詳細

変換は次のように与えられます

  * $$
    G_{mol} = G_{ms}  \, pressure / (Rgas  Tair)
    $$
  * $$
    G_{ms} = G_{mol}  \, (Rgas  Tair) / pressure
    $$

ここで、Tair はケルビンで、圧力は Pa（内部で kPa から変換されます）。

# 参考文献

Jones, H*G* 1992_ Plants and microclimate: a quantitative approach to    environmental plant physiology_   2nd Edition*, Cambridge University Press, Cambridge* 428 

# 例

```jldoctest; output = false
G_ms,Tair,pressure = 0.005,25.0,100.0
rmol = ms_to_mol(G_ms,Tair,pressure)
≈(rmol, 0.2017, atol =1e-4)
# output
true
```
