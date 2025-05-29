```
sparse_jacobian(ad::AbstractADType, cache::AbstractMaybeSparseJacobianCache, f, x)
sparse_jacobian(ad::AbstractADType, cache::AbstractMaybeSparseJacobianCache, f!, fx, x)
```

スパース性検出 `cache` を使用してスパースヤコビアンを計算します。これは、各関数呼び出しで新しいヤコビアンを割り当てます。

`x` が StaticArray の場合、この関数はヤコビアン計算のために非割り当て実装を使用しようとします。これは現在、限られたバックエンドでのみ可能です。
