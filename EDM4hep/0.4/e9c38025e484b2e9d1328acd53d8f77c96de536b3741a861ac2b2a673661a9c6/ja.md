再構成された粒子

  * 著者: F.Gaede, DESY

# フィールド

  * `type::Int32`: 再構成された粒子のタイプ。再構成された粒子のタイプ名と値のコレクションパラメータを確認/設定します。
  * `energy::Float32`: [GeV] 再構成された粒子のエネルギー。四運動量状態は内部で一貫性が保たれていません。
  * `momentum::Vector3f`: [GeV] 粒子の運動量。四運動量状態は内部で一貫性が保たれていません。
  * `referencePoint::Vector3f`: [mm] 参照点、すなわち粒子が測定された場所
  * `charge::Float32`: 再構成された粒子の電荷。
  * `mass::Float32`: [GeV] 再構成された粒子の質量、四ベクトルとは独立して設定されます。四運動量状態は内部で一貫性が保たれていません。
  * `goodnessOfPID::Float32`: [0;1] のスケールでのPIDの全体的な良さ
  * `covMatrix::SVector{10,Float32}`: 再構成された粒子の4ベクトルの共分散行列（10パラメータ）。四運動量の下三角行列（px,py,pz,E）として保存されます。すなわち、cov(px,px), cov(py,##

# 関係

  * `startVertex::Vertex`: この粒子に関連付けられた開始頂点
  * `particleIDUsed::ParticleID`: この粒子の運動学に使用された粒子ID
  * `clusters::Cluster`: この粒子に使用されたクラスタ。
  * `tracks::Track`: この粒子に使用されたトラック。
  * `particles::ReconstructedParticle`: この粒子に結合された再構成された粒子。
  * `particleIDs::ParticleID`: 粒子ID（その尤度によってソートされていない）

# メソッド

  * `pushToClusters(obj::ReconstructedParticle, robj::Cluster)`: 関連オブジェクトを `clusters` 関係にプッシュします
  * `popFromClusters(obj::ReconstructedParticle)`: `clusters` 関係から最後の関連オブジェクトをポップします
  * `pushToTracks(obj::ReconstructedParticle, robj::Track)`: 関連オブジェクトを `tracks` 関係にプッシュします
  * `popFromTracks(obj::ReconstructedParticle)`: `tracks` 関係から最後の関連オブジェクトをポップします
  * `pushToParticles(obj::ReconstructedParticle, robj::ReconstructedParticle)`: 関連オブジェクトを `particles` 関係にプッシュします
  * `popFromParticles(obj::ReconstructedParticle)`: `particles` 関係から最後の関連オブジェクトをポップします
  * `pushToParticleIDs(obj::ReconstructedParticle, robj::ParticleID)`: 関連オブジェクトを `particleIDs` 関係にプッシュします
  * `popFromParticleIDs(obj::ReconstructedParticle)`: `particleIDs` 関係から最後の関連オブジェクトをポップします
