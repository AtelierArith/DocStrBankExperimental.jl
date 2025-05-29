```
function krylov_extend!(psi::MPS, H::MPO; kwargs...)
```

グローバル部分空間拡張を実行します。

#### 名前付き引数とそのデフォルト値:

  * `extension_krylovdim::Int = 3`: GSEに使用されるKrylovベクトルの数。
  * `extension_applyH_cutoff::Float64 = Float64_threshold()`: MPOをMPSに適用する際のカットオフ。
  * `extension_applyH_maxdim::Int = maxlinkdim(psi) + 1`: MPOをMPSに適用した後の結果のMPSの最大ボンド/リンク次元。
  * `extension_cutoff::Float64 = 1E-10`: GSEにおける基底拡張ステップのカットオフ。
