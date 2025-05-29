```
AffineMap <: AbstractAffineMap
```

具体的なアフィン変換です。マッピング `x -> M*x + v` を構築するには、次のようにします。

```
AffineMap(M, v)
```

ここで `M` は行列、`v` はベクトルです。任意の `Transformation` は、点 `x` の周りで線形化することによってアフィン近似に変換できます。

```
AffineMap(trans, [x])
```

すでにアフィンである変換の場合、`x` は省略できます。
