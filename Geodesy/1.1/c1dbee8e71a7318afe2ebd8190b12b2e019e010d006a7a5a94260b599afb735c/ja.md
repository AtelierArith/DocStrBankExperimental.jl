```
UTMfromLLA(zone, isnorth::Bool, datum)
```

指定されたゾーンと半球（`isnorth = true` または `false`）で、グローバルな `LLA` 座標を `UTM` 座標に変換するための `Transformation` オブジェクトを構築します。効率のために楕円体パラメータを事前にキャッシュし、チャールズ・カーニーの正確な6次の級数展開アルゴリズムを実行します。

（`UTMZfromLLA` も参照）
