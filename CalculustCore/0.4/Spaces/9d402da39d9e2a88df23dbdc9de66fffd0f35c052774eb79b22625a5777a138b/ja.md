```
transformOp(V::AbstractSpace)
```

ベクトルを `V` から `transform(V)` に移す変換演算子を取得します。変換演算子を異なる `AbstractVecOrMat` サブタイプに作用させるには、次のように呼び出します。

```
V = make_transform(V, input_prototype)
```
