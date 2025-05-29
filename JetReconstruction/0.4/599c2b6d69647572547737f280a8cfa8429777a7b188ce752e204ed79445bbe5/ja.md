```
PseudoJet(px::Real, py::Real, pz::Real, E::Real,
    _cluster_hist_index::Int,
    pt2::Real)
```

与えられた運動量成分とエネルギーおよび履歴インデックスを使用して、PseudoJetオブジェクトを構築します。

# 引数

  * `px::Real`: 運動量のx成分。
  * `py::Real`: 運動量のy成分。
  * `pz::Real`: 運動量のz成分。
  * `E::Real`: エネルギー。
  * `_cluster_hist_index::Int`: クラスタ履歴インデックス。
  * `pt2::Real`: 横運動量の二乗。

# 戻り値

`PseudoJet`オブジェクト。
