```
get_cape_and_outflow_temp_from_sounding(tparcel :: Real, 
rparcel :: Real, 
pparcel :: Real,
t Array{<: Real},
r Array{<: Real},
p Array{<: Real}, ptop=50u"hPa")
```

熱力学プロファイルからcape、アウトフロー温度、および中立浮力のインデックスを計算します。
