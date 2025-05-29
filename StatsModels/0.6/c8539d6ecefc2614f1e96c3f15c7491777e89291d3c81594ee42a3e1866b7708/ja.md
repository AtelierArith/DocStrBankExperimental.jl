```
modelcols(t::AbstractTerm, data)
```

`AbstractTerm`に基づいてデータの数値的な「モデル列」表現を作成します。`data`は、全体のテーブル（[Tables.jl](https://github.com/JuliaData/Tables.jl)によって定義された、プロパティアクセス可能な反復可能な列のコレクションまたはプロパティアクセス可能な行の反復可能なコレクション）であるか、スカラー値の`NamedTuple`の形をした単一の行であることができます。テーブルは`Vectors`の`NamedTuple`に変換されます（例：`Tables.ColumnTable`）。
