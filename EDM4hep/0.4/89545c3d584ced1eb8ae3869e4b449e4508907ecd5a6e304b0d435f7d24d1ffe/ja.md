Vertex

  * 著者: F.Gaede, DESY

# フィールド

  * `primary::Int32`: ブールフラグ、イベントの主頂点である場合
  * `chi2::Float32`: 頂点フィットのカイ二乗
  * `probability::Float32`: 頂点フィットの確率
  * `position::Vector3f`: [mm] 頂点の位置。
  * `covMatrix::SVector{6,Float32}`: 位置の共分散行列（下三角行列として保存、すなわち cov(xx),cov(y,x),cov(z,x),cov(y,y),... )
  * `algorithmType::Int32`: 頂点を作成するために使用されたアルゴリズムのタイプコード - コレクションパラメータ AlgorithmName と AlgorithmType を確認/設定してください。
  * `parameters::PVector{Float32}`: この頂点に関連する追加のパラメータ - パラメータの意味についてはコレクションパラメータ "VertexParameterNames" を確認/設定してください。

# 関係

  * `associatedParticle::POD`: この頂点に関連付けられた再構成された粒子。

# メソッド

  * `setParameters(object::Vertex, v::AbstractVector{Float32})`: `parameters` ベクターメンバーに値のセットを割り当てる
