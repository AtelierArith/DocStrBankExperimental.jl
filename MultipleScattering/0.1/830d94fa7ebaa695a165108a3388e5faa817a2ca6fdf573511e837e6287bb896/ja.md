```
run(sim::FrequencySimulation, region::Shape;
    res=20, xres=res, yres=res, basis_order=5)
```

シミュレーション `sim` を領域内の位置のグリッドと角周波数 `ω` に対して実行します。

周波数は浮動小数点数または浮動小数点数のベクトルであることができます。グリッドポイントの解像度は xres と yres によって定義されます。
