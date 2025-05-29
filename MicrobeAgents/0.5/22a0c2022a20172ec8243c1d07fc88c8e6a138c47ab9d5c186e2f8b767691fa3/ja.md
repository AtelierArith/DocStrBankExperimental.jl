```
Microbe{D,N} <: AbstractMicrobe{D,N}
```

シンプルなシミュレーションのための基本的な微生物タイプです。`D`は空間の次元数で、`N`は微生物の運動パターンの状態数です。

`Microbe`には必要なフィールドがあります。

  * `id::Int` 内部で使用される識別子
  * `pos::SVector{D,Float64}` 空間的位置
  * `vel::SVector{D,Float64}` 単位速度ベクトル
  * `speed::Float64` 速度ベクトルの大きさ
  * `motility::Motility{N}` 運動パターン

およびデフォルトのパラメータ

  * `rotational_diffusivity::Float64 = 0.0` ブラウン運動の回転拡散の係数
  * `radius::Float64 = 0.0` 微生物の等価球半径
  * `state::Float64 = 0.0` スカラー内部状態のための一般的な変数
