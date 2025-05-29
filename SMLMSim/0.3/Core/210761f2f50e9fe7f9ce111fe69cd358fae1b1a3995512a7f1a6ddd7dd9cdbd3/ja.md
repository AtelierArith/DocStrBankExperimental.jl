```
GenericFluor(; photons::AbstractFloat=1e5, k_off::AbstractFloat=50.0, k_on::AbstractFloat=1e-2)
```

指定されたパラメータを持つシンプルな2状態（オン/オフ）フルオロフォアを作成します。

# 引数

  * `photons::AbstractFloat`: 光子放出率（Hz）
  * `k_off::AbstractFloat`: オフスイッチング率（オン→オフ）（Hz）
  * `k_on::AbstractFloat`: オンスイッチング率（オフ→オン）（Hz）

# 詳細

指定されたレートを持つ2状態モデルのフルオロフォアを作成します。状態1はオン（明るい）状態で、状態2はオフ（暗い）状態です。レート行列は次のように構築されます: q = [-k*off k*off; k*on -k*on]
