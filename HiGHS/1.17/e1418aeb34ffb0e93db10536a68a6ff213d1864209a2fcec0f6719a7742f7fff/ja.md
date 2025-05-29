```
Highs_clear(highs)
```

オプションをリセットし、その後 `clearModel` を呼び出します。

すべての関連メモリを解放するには [`Highs_destroy`](@ref) を参照してください。

### パラメータ

  * `highs`: Highs インスタンスへのポインタ。

### 戻り値

呼び出しが成功したかどうかを示す `kHighsStatus` 定数。
