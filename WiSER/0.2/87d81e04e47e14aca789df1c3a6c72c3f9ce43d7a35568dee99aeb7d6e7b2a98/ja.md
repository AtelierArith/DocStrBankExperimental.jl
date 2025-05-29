```
WSVarLmmModel(meanformula::FormulaTerm, reformula::FormulaTerm, 
wsvarformula::FormulaTerm, idvar::Union{String, Symbol}, tbl)
```

`WSVarLmmModel`のコンストラクタは、Tables.jl互換のソースから作成されます。

# 位置引数

  * `meanformula`: 平均固定効果βのための式（X行列の変数）。
  * `reformula`: 平均ランダム効果γのための式（Z行列の変数）。
  * `wsvarformula`: 被験者内分散効果τのための式（W行列の変数）。
  * `idvar`: グループ化のためのID変数。
  * `tbl:` モデルのためのすべてのデータを保持するデータテーブル。`DataFrame`またはJuliaDBの`IndexedTable`のような列ベースのテーブルであることができます。

# キーワード引数

  * `wtvar`: データテーブル内の観測重みと対応する変数名。

# 例

```
vlmm3 = WSVarLmmModel(@formula(y ~ 1 + x2 + x3 + x4 + x5),
    @formula(y ~ 1 + z2 + z3), @formula(y ~ 1 + w2 + w3 + w4 + w5), "id", df)
```
