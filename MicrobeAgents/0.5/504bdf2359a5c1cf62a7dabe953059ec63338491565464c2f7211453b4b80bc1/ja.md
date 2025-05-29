```
AbstractMicrobe{D} <: AbstractAgent where {D<:Integer}
```

MicrobeAgents.jlシミュレーション内のすべての微生物タイプは、`AbstractMicrobe`のサブタイプであるユーザー定義型のインスタンスでなければなりません。     YourMicrobeType{D} <: AbstractMicrobe{D} パラメータ`D`は、微生物タイプが存在する空間の次元（1、2、3がサポートされています）を定義します。

すべての微生物タイプは*少なくとも*以下のフィールドを持たなければなりません：

  * `id::Int` 微生物のID（Agents.jlによって内部的に使用される）
  * `pos::SVectpr{D,Float64}` 微生物の位置
  * `vel::SVector{D,Float64}` 微生物の速度
  * `motility::AbstractMotility` 微生物の運動パターン
  * `turn_rate::Real` 微生物の平均再方向転換率
  * `rotational_diffusivity::Real` ブラウン運動の回転拡散係数
  * `radius::Real` 微生物の等価球半径
  * `state::Real` スカラー内部状態のための汎用変数
