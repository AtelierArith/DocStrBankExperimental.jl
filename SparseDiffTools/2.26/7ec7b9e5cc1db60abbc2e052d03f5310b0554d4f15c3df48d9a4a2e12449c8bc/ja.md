```
sparse_jacobian(ad::AbstractADType, sd::AbstractMaybeSparsityDetection, f, x; fx=nothing)
sparse_jacobian(ad::AbstractADType, sd::AbstractMaybeSparsityDetection, f!, fx, x)
```

`sparse_jacobian_cache` と `sparse_jacobian!` を順次呼び出して、`x` における `f` のヤコビ行列を計算します。`f` のヤコビ行列が正確に1回だけ計算される場合にこれを使用します。それ以外の場合は、キャッシュを生成するために `sparse_jacobian_cache` を1回使用し、同じキャッシュを使ってヤコビ行列を計算するために `sparse_jacobian!` を使用します。

`x` が StaticArray の場合、この関数はヤコビ行列計算のために非アロケーション実装を使用しようとします。これは現在、限られたバックエンドでのみ可能です。
