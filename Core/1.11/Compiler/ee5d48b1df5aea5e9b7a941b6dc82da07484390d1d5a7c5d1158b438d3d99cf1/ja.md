```
struct NotFound end
const NOT_FOUND = NotFound()
```

変数がまだ分析されていないことを表す特別なシングルトンです。特に、すべてのSSA値タイプは、新しい`InferenceState`を作成する際に`NOT_FOUND`として初期化されます。これは`VarTable`の抽象状態を更新する`smerge`のみに使用されるため、これに対する格子は定義しません。
