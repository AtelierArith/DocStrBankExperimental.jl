```
mutable struct PseudoJet <: FourMomentum
```

`PseudoJet`構造体は、ジェット再構成アルゴリズムで使用される四運動量オブジェクトである擬似ジェットを表します。クラスタリングの履歴に戻るための追加情報は、`_cluster_hist_index`フィールドに保存されます。ラピディティと方位角の計算のうち、より高価な計算はキャッシュされており、迅速にアクセスできます。

# フィールド

  * `px::Float64`: 運動量のx成分。
  * `py::Float64`: 運動量のy成分。
  * `pz::Float64`: 運動量のz成分。
  * `E::Float64`: 運動量のエネルギー成分。
  * `_cluster_hist_index::Int`: クラスタ履歴のインデックス。
  * `_pt2::Float64`: 二乗横運動量。
  * `_inv_pt2::Float64`: 逆二乗横運動量。
  * `_rap::Float64`: ラピディティ。
  * `_phi::Float64`: 方位角。
