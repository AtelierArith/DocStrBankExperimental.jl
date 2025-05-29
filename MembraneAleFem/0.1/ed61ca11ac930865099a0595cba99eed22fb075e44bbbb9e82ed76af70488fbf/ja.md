```
動き
```

メッシュ動作の種類: `instances(Motion)`

  * `STATIC = 1` –> メッシュは動かない
  * `EUL    = 2` –> オイラー的メッシュ動作
  * `LAG    = 3` –> ラグランジュ的メッシュ動作
  * `ALEV   = 4` –> ALE粘性メッシュ動作
  * `ALEVB  = 5` –> ALE粘性曲げメッシュ動作

動作の選択は、[`Params.jl`](@ref man-params)の`Params.motion`変数に保存され、[`Bc.jl`](@ref man-mesh)における境界条件の仕様や[有限要素解析](@ref man-analysis)に関連しています。
