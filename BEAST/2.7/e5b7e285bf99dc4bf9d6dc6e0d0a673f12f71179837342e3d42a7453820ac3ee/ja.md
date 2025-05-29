```
quaddata(operator, test_refspace, trial_refspace, test_elements, trial_elements)
```

境界要素相互作用の計算に必要なデータをキャッシュするオブジェクトを返します。どのデータをキャッシュするかはクライアントプログラマーの判断に委ねられています。例えば、二重数値積分の場合、積分点を保存することで行列の組み立てを大幅に高速化できます。

  * `operator` は積分カーネルです。
  * `test_refspace` と `trial_refspace` は参照空間オブジェクトです。`quaddata`

は通常、これらの局所的な形状関数の空間の型に対してオーバーロードされます。（例として `maxwell.jl` の実装を参照してください）。

  * `test_elements` と `trial_elements` は、有限要素空間が定義されている幾何学的要素の反復可能なコレクションです。これらは、座標だけでなく実際の積分点の計算を可能にするために提供されています。
