```
PrecomputedJacobianColorvec(; jac_prototype, partition_by_rows::Bool = false,
    colorvec = missing, row_colorvec = missing, col_colorvec = missing)
```

スパース微分に直接使用できる事前に指定された `colorvec` を使用します。逆モード、前方モード、または有限差分が使用されるかに基づいて、対応する `row_colorvec` または `col_colorvec` が使用されます。これらのうちの1つだけが `nothing` に設定できます。

## キーワード引数

```
- `jac_prototype`: 構造的非ゼロを計算するために使用されるプロトタイプヤコビアン
- `partition_by_rows`: ヤコビアンを行または列で分割するかどうか（行分割は逆モードADに使用されます）
- `colorvec`: ヤコビアンのcolorvec。`partition_by_rows` が `true` の場合、これは行colorvecであり、そうでない場合は列colorvecです
- `row_colorvec`: ヤコビアンの行colorvec
- `col_colorvec`: ヤコビアンの列colorvec
```

関連情報: [SymbolicsSparsityDetection](@ref), [JacPrototypeSparsityDetection](@ref)
