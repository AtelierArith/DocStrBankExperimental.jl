モジュール全体のグローバルな EarthOrientationData オブジェクト。このデータオブジェクトは、明示的な EarthOrientationData ファイルがそれらの変換に提供されていない場合、参照システム変換によって Earth Orientation Data のデフォルトソースとして使用されます。

この値は、次のように自分のコードで上書きできます：

```julia
SatelliteDynamics.EOP = EarthOrientationData(:FINALS_2000)
```

このグローバル変数は、他に設定/提供されていない場合、モジュールの内部バージョンの `"FINALS_2000"` を使用することがデフォルトです。
