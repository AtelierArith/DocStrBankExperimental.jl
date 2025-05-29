```
Highs_destroy(highs)
```

`highs`によって作成されたモデルを[`Highs_create`](@ref)によって破棄し、対応するすべてのメモリを解放します。`highs`を使用した将来の呼び出しは許可されていません。

`highs`を無効にせずにモデルを空にするには、[`Highs_clearModel`](@ref)を参照してください。

### パラメータ

  * `highs`: Highsインスタンスへのポインタ。
