```
forward(F::MRSForward, m::Vector{<:Real})
```

与えられたFID実験設定に対する水分モデルの複素応答振幅を計算します。これは`MRSForward`オブジェクトで説明されます。応答は複素ベクトルとして返され、単位はボルトで、パルスモーメントごとに1つの要素があります。

パラメータ:

  * `F`: モデリングのためのカーネルを含む`MRSForward`オブジェクト
  * `m`: `F.zgrid`の各深さにおける水分飽和を含むベクトル

```
