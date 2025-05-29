```
transformOp(V::AbstractSpace)
```

`V`から`transform(V)`へのベクトルを取る変換演算子を取得します。異なる`AbstractVecOrMat`サブタイプに作用するように変換演算子を変更するには、次のように呼び出します。

```
V = make_transform(V, input_prototype)
```
