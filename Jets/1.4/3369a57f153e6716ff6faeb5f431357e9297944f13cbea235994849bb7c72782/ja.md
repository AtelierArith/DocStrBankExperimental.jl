```
JetSSpace(_T, n, M, map::F)
```

対称空間 `JetSSpace` を構築して返します。

# パラメータ

  * `_T` は型で、通常は `Complex{Float32}` または `Complex{Float64}` です。
  * `n` は空間の次元を定義するタプルです。
  * `M` はどの次元が対称であるかを定義するタプルです。現在のところ、APIでは単一の対称次元のみがサポートされています。
  * `F` は、以下に説明する対称次元のインデックスをマッピングする関数です。

`JetSSpace` を必要とする例はフーリエ変換です：実ベクトルのフーリエ変換は、エルミート対称性を持つ複素空間にあります。正の周波数のみが必要で、負の周波数のスペクトルは対応する正の周波数のスペクトルのエルミート共役です：`S(-f) = conj(S(f))`。この例では、マップ `F` は `-f` の多次元インデックスが与えられたときに `f` の多次元インデックスを返す関数です。

関連情報：`JetPackTransforms` パッケージの `JopFft`。
