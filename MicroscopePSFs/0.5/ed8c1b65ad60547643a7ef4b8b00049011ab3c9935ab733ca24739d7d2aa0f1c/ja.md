```
VectorPupilFunction{T}
```

ベクトル瞳関数は、PupilFunctionsとしてEx、Eyフィールド成分を格納します。

# フィールド

  * `nₐ::T`: 数値開口
  * `λ::T`: 波長（μm単位）
  * `n_medium::T`: サンプル媒体の屈折率
  * `n_coverslip::T`: カバーガラスの屈折率
  * `n_immersion::T`: 没入媒体の屈折率
  * `Ex::PupilFunction{T}`: 電場のx成分
  * `Ey::PupilFunction{T}`: 電場のy成分
