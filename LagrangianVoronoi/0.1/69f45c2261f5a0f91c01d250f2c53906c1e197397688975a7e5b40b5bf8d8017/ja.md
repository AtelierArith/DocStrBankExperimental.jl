```
SimulationWorkspace
```

計算グリッド、ソルバー、およびグローバル変数を含むための抽象型。このメソッドは、SimulationWorkspaceのインスタンス`sim`に対して定義されるべきです：

  * step!(sim, time::Float64)
  * postproc!(sim, time::Float64) [オプション]
