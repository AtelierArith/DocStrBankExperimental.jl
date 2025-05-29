```
struct DataMatrix{T,Tv,To}
```

`DataMatrix`は、変数と観察の注釈と共に行列を表します。

フィールド:

  * `matrix::T` - 行列。
  * `var::Tv` - 変数の注釈。
  * `obs::To` - 観察の注釈。
  * `models::Vector{ProjectionModel}` - この`DataMatrix`の作成に使用されるモデル。

`var`および`obs`テーブルの最初の列には、一意のIDが含まれている必要があります。
