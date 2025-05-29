```
JacPrototypeSparsityDetection(; jac_prototype, alg = GreedyD1Color())
```

事前に指定された `jac_prototype` を使用して、ヤコビ行列の行列色を計算します。

## キーワード引数

```
- `jac_prototype`: 行列色を計算するために使用されるプロトタイプヤコビ行列
- `alg`: 行列色を計算するために使用されるアルゴリズム
```

関連情報: [SymbolicsSparsityDetection](@ref), [PrecomputedJacobianColorvec](@ref)
