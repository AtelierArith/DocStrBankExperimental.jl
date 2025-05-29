```
localvariography(sdata, lpars, var₁, var₂=var₁;
axis=:X, tol=1e-6, maxratio1=Inf, maxratio2=Inf, [optional parameters])
```

空間データ`sdata`の変数`var₁`と`var₂`のための非従来型の方向性（交差）バリオグラムを計算します。これは、ローカルな`axis`方向（`axis` ∈ [:X, :Y, :Z]）に沿った擬似パーティションを作成するためにローカル異方性`lpars`を使用し、これらのデータを用いてEmpiricalVariogramが計算されます。方向性の許容帯域幅`tol`を渡すことができます。`maxratio1`と`maxratio2`は、これらの値を超える大きさの比率がある場合にデータを部分的に無視します（デフォルトでは何も無視しません）。その他のオプションのパラメータは、`GeoStats.EmpiricalVariogram`で定義されており、`nlags`、`maxlag`、`distance`、`algo`などがあります。指定された軸が2つの軸の組み合わせ（例：:XY）の場合、これはその平面に沿った平面バリオグラムを考慮します。

https://github.com/rmcaixeta/Local_variographyに似ていますが、同じではありません。
