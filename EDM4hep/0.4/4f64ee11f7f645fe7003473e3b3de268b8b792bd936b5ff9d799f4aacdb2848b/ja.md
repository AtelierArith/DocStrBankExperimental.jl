dN/dx または dE/dx のトラック情報。

  * 著者: Wenxing Fang, IHEP

# フィールド

  * `dQdx::Quantity`: 再構成された dEdx または dNdx とその誤差
  * `particleType::Int16`: 粒子の種類、e(0)、mu(1)、pi(2)、K(3)、p(4)。
  * `type::Int16`: 種類。
  * `hypotheses::SVector{5,Hypothesis}`: 5 粒子仮説
  * `hitData::PVector{HitLevelData}`: ヒットレベルデータ

# 関係

  * `track::Track`: 対応するトラック。

# メソッド

  * `setHitData(object::RecDqdx, v::AbstractVector{HitLevelData})`: `hitData` ベクターメンバーに値のセットを割り当てる
