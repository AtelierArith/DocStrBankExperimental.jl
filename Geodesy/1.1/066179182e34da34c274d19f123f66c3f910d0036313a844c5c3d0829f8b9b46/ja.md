```
LLAfromUTM(zone, isnorth::Bool, datum)
```

指定されたゾーンと半球（`isnorth = true` または `false`）の `UTM` 座標からグローバル `LLA` 座標に変換する `Transformation` オブジェクトを構築します。効率のために楕円体パラメータを事前にキャッシュし、チャールズ・カーニーの正確な6次の級数展開アルゴリズムを実行します。

（`LLAfromUTMZ` も参照）
