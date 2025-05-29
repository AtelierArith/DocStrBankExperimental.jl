```
applyreduce(f, op, target::Union{TraitTarget, GI.AbstractTrait}, obj; threaded, init, kw...)
```

関数 `f` を `target` 特性を持つすべてのオブジェクトに適用し、結果を `+` のような `op` で減算します。

`op` の適用の順序とグループ化は保証されていません。

`threaded==true` の場合、配列や反復可能なオブジェクト、特徴コレクション、ネストされたジオメトリに対してスレッドが使用されます。

`init` は、`reduce` のようなベースのJulia関数での動作と同じです。
