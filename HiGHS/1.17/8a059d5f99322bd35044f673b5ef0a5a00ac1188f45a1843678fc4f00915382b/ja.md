```
Highs_writeSolution(highs, filename)
```

解決策情報（利用可能な場合は双対および基準状態を含む）をファイルに書き込みます。

参照: [`Highs_writeSolutionPretty`](@ref)。

### パラメータ

  * `highs`: Highsインスタンスへのポインタ。
  * `filename`: 結果を書き込むファイルの名前。

### 戻り値

呼び出しが成功したかどうかを示す `kHighsStatus` 定数。
