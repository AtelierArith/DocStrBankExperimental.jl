```
evaluate(tsg::TasmanianSG, x)
```

は、関心のある単一のポイントで補間関数を評価し、結果を返します。これは、選択された加速タイプを使用した加速バージョンですが、スレッドセーフではない可能性があります。

これは、グリッドが作成された後、値がロードされた後に呼び出されるべきです。

x: getNumDimensions() の長さを持つベクトル    エントリは、重みを評価するためのポイントを示します。

出力: getNumOutputs() の長さを持つベクトルを返します         fX における補間関数の値。
