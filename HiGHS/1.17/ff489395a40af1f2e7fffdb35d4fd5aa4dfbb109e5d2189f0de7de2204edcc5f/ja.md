```
Highs_writeSolutionPretty(highs, filename)
```

解決策情報（利用可能な場合は双対および基準状態を含む）を人間が読みやすい形式でファイルに書き込みます。

このメソッドは[`Highs_writeSolution`](@ref)と同一ですが、出力は人間が読みやすい形式です。

### パラメータ

  * `highs`: Highsインスタンスへのポインタ。
  * `filename`: 結果を書き込むファイルの名前。

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。
