```
setup(
    sources::Matrix{F},
    targets::Matrix{F},
    fmmoptions::HelmholtzFMMOptions{I, C}
) where {I, F <: Real, C <: Complex}
```

C++部分でFMM構造を設定し、すべての必須ストレージを割り当てます。

# 引数

  * `sources::Matrix{F}`: ソースの3D座標。
  * `targets::Matrix{F}`: ターゲットの3D座標。
  * `fmmoptions::HelmholtzFMMOptions{I, C}`: セットアップ関数のためのJulia Helmoltz初期化子。
