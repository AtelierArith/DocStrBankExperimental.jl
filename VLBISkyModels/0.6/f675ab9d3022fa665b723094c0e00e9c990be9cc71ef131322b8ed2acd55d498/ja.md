```
FourierDualDomain(imgdomain::AbstractRectiGrid, alg::FFTAlg)
```

FFTアルゴリズムを使用して変換を計算するFourierDualDomainを構築します。この場合、[`FFTAlg`](@ref)で指定されたパディングを持つFFTのデフォルトグリッドであると仮定するため、可視性ドメインは指定されていません。

## 引数

  * `imgdomain`: 画像ドメイングリッド
  * `alg`: 使用するFFTアルゴリズム
