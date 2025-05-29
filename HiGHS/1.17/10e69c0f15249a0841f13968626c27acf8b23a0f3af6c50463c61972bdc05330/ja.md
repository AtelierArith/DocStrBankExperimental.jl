```
Highs_clearSolver(highs)
```

モデルに関連付けられたすべての解データをクリアします。

モデルをクリアし、関連するすべてのメモリを解放するには、[`Highs_destroy`](@ref)を参照してください。

### パラメータ

  * `highs`: Highsインスタンスへのポインタ。

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。
