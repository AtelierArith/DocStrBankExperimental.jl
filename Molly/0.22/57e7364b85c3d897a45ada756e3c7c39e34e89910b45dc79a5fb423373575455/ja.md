```
AndersenThermostat(temperature, coupling_const)
```

温度を制御するためのアンダーセンサーモスタット。

各原子の速度は、マクスウェル・ボルツマン分布から引かれた速度に、確率 `dt / coupling_const` で毎タイムステップごとにランダムに変更されます。詳細は[Andersen 1980](https://doi.org/10.1063/1.439486)を参照してください。
