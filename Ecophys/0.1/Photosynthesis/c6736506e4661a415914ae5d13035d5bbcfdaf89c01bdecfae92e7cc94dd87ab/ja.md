```
photosynthesis(par::C3, PAR = 1000.0, RH = 0.75, Tleaf = 298.0, Ca = 400.0, O2 = 210e3, gb = 0.5, net = true)
photosynthesis(par::C4, PAR = 1000.0, RH = 0.75, Tleaf = 298.0, Ca = 400.0, O2 = 210e3, gb = 0.5, net = true)
photosynthesis(par::C3Q, PAR = 1000.0μmol/m^2/s, RH = 0.75, Tleaf = 298.0K, Ca = 400.0μmol/mol, O2 = 210e3μmol/mol, gb = 0.5mol/m^2/s, net = true)
photosynthesis(par::C4Q, PAR = 1000.0μmol/m^2/s, RH = 0.75, Tleaf = 298.0K, Ca = 400.0μmol/mol, O2 = 210e3μmol/mol, gb = 0.5mol/m^2/s, net = true)
```

ネットまたは総CO2同化（umol/m2/s）とCO2のフラックスに対する気孔導電率（mol/m2/s）を光合成活性放射（PAR, umol/m2/s）、相対湿度（RH）、葉温度（Tleaf, K）、空気中のCO2部分圧（Ca, μmol/mol）、酸素（O2, μmol/mol）、およびCO2に対する境界層導電率（gb, mol/m2/s）の関数として計算します。環境入力はスカラーでなければなりません。引数`net`は、ネットまたは総CO2同化を返すべきかを示します。
