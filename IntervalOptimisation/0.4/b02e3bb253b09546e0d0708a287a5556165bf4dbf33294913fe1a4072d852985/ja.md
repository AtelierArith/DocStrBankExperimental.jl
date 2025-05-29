```
最小化(f, X, structure = SortedVector, tol=1e-3)
または
最小化(f, X, structure = HeapedVector, tol=1e-3)
または
最小化(f, X, tol=1e-3) この場合、"structure" のデフォルト値は "HeapedVector" です
```

`f` のグローバル最小値を `Interval` または `IntervalBox` `X` 上でモーア-スケルボーアルゴリズムを使用して求めます。ベクトル要素の配置方法は、ヒープ配列またはソート配列のいずれかです。ベクトル要素の配置方法を特に指定しない場合は、デフォルトでヒープ配列が使用されます。

高次元関数 $f:\mathbb{R}^n \to \mathbb{R}$ の場合、`f` は単一のベクトル引数を取る必要があります。

グローバル最小値を含む区間と、最小化を含むボックスのリストを返します。
