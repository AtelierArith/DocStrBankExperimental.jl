```
umolCO2_to_gC(CO2_flux; constants=BigleafConstants())
gC_to_umolCO2(C_flux; constants=BigleafConstants())
```

CO2の量を(umol CO2 m-2 s-1)から(g C m-2 d-1)に、またその逆に変換します。

# 引数

  * CO2_flux  CO2フラックス (umol CO2 m-2 s-1)
  * C_flux    炭素 (C) フラックス (gC m-2 d-1)
  * `constants`: [`BigleafConstants`](@ref) からの辞書で、エントリには: Cmol, umol2mol, mol2umol, kg2g, g2kg, says2seconds

# 例

```@example
umolCO2_to_gC(20)  # gC m-2 d-1
```
