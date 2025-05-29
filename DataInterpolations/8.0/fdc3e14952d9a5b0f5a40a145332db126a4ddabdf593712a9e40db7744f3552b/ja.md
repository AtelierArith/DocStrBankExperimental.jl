```
LagrangeInterpolation(u, t, n = length(t) - 1; extrapolation::ExtrapolationType.T = ExtrapolationType.None, 
extrapolation_left::ExtrapolationType.T = ExtrapolationType.None, extrapolation_right::ExtrapolationType.T = ExtrapolationType.None)
```

これは、データポイントすべてを通過する(k-1)次のラグランジュ多項式を使用した補間の方法です。ここで、kはデータポイントの数です。

## 引数

  * `u`: データポイント。
  * `t`: 時間ポイント。
  * `n`: 多項式の次数。現在は(k-1)次のみで、kはデータポイントの数です。

## キーワード引数

  * `extrapolation`: データの左側と右側に適用される外挿タイプ。可能なオプションは、`ExtrapolationType.None`（デフォルト）、`ExtrapolationType.Constant`、`ExtrapolationType.Linear`、`ExtrapolationType.Extension`、`ExtrapolationType.Periodic`、および`ExtrapolationType.Reflective`です。
  * `extrapolation_left`: データの左側に適用される外挿タイプ。可能なオプションについては`extrapolation`を参照してください。このキーワードは、`extrapolation != Extrapolation.none`の場合は無視されます。
  * `extrapolation_right`: データの右側に適用される外挿タイプ。可能なオプションについては`extrapolation`を参照してください。このキーワードは、`extrapolation != Extrapolation.none`の場合は無視されます。
