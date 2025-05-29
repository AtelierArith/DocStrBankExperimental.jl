```
seasonal_decomposition(A::ClimArray, fs = [1, 2]) → seasonal, residual
```

`A`を季節成分と残差成分に分解します。季節成分には`A`の周期的な部分が含まれ、周波数は`fs`で指定され、残差成分には残りの部分が含まれます。

`fs`は1年あたりで測定されます。この関数は非等間隔の時間軸（例：月次平均）でも機能し、LPVSpectral.jlおよびSignalDecomposition.jlを使用します。
