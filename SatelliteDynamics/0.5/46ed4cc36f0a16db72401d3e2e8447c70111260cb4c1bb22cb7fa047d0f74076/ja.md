モジュール全体のグローバルGravityModelオブジェクト。このデータオブジェクトは、他に提供されない限り、デフォルトの球面調和重力場として使用されます。

この値は、次のように自分のコードで上書きできます。

```julia
SatelliteDynamics.GravityModel = GravityModel(PATH_TO_YOUR_GRAVITY_MODEL)
```

このグローバル変数は、他に設定されていない場合、モジュールの内部バージョンのEGM2008モデルを次数と次数90に切り捨てて使用することがデフォルトです。
