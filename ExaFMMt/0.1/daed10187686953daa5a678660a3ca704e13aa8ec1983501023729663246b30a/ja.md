```
setup(
    sources::Matrix{F},
    targets::Matrix{F},
    fmmoptions::ModifiedHelmholtzFMMOptions{I, F}
) where {I, F <: Real}
```

C++ 部分で FMM 構造を設定し、すべての必須ストレージを割り当てます。

# 引数

  * `sources::Matrix{F}`: ソースの 3D 座標。
  * `targets::Matrix{F}`: ターゲットの 3D 座標。
  * `fmmoptions::ModifiedHelmholtzFMMOptions{I, F}`: setup 関数のための Julia 修正ヘルムホルツ初期化子。
