```
UTMZfromLLA(datum)
```

グローバルな `LLA` 座標からグローバルな `UTMZ` 座標に変換するための `Transformation` オブジェクトを構築します。ゾーンと半球は、標準定義（ノルウェーの例外を含む）に従って自動的に計算されます。効率のために楕円体パラメータを事前にキャッシュし、チャールズ・カーニーの正確な6次の級数展開アルゴリズムを実行します。

（`UTMfromLLA` も参照してください）
