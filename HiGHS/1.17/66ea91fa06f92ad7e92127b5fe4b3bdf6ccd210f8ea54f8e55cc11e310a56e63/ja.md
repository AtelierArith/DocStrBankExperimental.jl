```
Highs_zeroAllClocks(highs)
```

`highs` モデル内の時計をリセットします。

各 `highs` モデルには、アルゴリズムのさまざまな部分に費やされた時間を記録する単一の時計が含まれています。この時計は [`Highs_run`](@ref) に入るときにリセットされないため、[`Highs_run`](@ref) への繰り返しの呼び出しは、アルゴリズムに費やされた累積時間を報告します。副作用として、累積実行時間が時間制限を超えると、各個別の [`Highs_run`](@ref) 呼び出しの実行時間ではなく、時間制限による終了がトリガーされます。

回避策として、各 [`Highs_run`](@ref) 呼び出しの前に [`Highs_zeroAllClocks`](@ref) を呼び出してください。

### パラメータ

  * `highs`: Highs インスタンスへのポインタ。

### 戻り値

呼び出しが成功したかどうかを示す `kHighsStatus` 定数。
