```
setup(
    sources::Matrix{F},
    targets::Matrix{F}, 
    fmmoptions::LaplaceFMMOptions{I}
) where {I, F <: Real}
```

C++部分でFMM構造を設定し、すべての必須ストレージを割り当てます。

# 引数

  * `sources::Matrix{F}`: ソースの3D座標。
  * `targets::Matrix{F}`: ターゲットの3D座標。
  * `fmmoptions::LaplaceFMMOptions{I}`: setup関数のためのJuliaラプラス初期化子。
