```
PrecomputedJacobianColorvec(jac_prototype, row_colorvec, col_colorvec)
```

スパース微分に直接使用できる事前に指定された `colorvec` を使用します。逆モード、前方モード、または有限差分のいずれが使用されるかに基づいて、対応する `row_colorvec` または `col_colorvec` が使用されます。どちらか一方だけが `nothing` に設定できます。

## 引数

```
- `jac_prototype`: 構造的非ゼロを計算するために使用されるプロトタイプヤコビ行列
- `row_colorvec`: ヤコビ行列の行カラーべクター
- `col_colorvec`: ヤコビ行列の列カラーべクター
```

関連項目: [SymbolicsSparsityDetection](@ref), [JacPrototypeSparsityDetection](@ref)
