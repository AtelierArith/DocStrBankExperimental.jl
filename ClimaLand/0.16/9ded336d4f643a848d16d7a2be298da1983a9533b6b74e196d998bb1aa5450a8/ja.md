```
AbstractImExModel{FT} <: AbstractModel{FT}
```

暗黙的に扱われる必要があるモデルのための抽象型（および明示的に扱うことができる傾向項を持つ可能性がある）。これは、AbstractModelからすべてのデフォルト関数定義を継承し、`make_imp_tendency`および`make_compute_imp_tendency`のデフォルトも継承します。
