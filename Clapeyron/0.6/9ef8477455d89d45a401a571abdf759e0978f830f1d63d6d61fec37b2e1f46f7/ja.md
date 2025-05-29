```
equivol_cross_second_virial(model::EoSModel,T,p_exp = 200000.0)
```

は、T,P条件で純ガスの等しい体積の混合をシミュレーションすることによって、第二交差ビリアル係数を計算します。各純ガスの等しい体積は、各成分の特定のモル量を設定します。実験の詳細は[1]にあります。

## 例

```
model = SAFTVRQMie(["helium","neon"])
B12 = equivol_cross_second_virial(model,)
```

## 参考文献

1. Brewer, J., & Vaughn, G. W. (1969). Measurement and correlation of some interaction second virial coefficients from − 125° to 50°C. I. The Journal of Chemical Physics, 50(7), 2960–2968. [doi:10.1063/1.1671491](https://doi.org/10.1063/1.1671491)
