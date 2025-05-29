カロリメーターヒットクラスター

  * 著者: F.Gaede, DESY

# フィールド

  * `type::Int32`: クラスターのタイプを定義するフラグワード。ビット16-31は内部で使用されます。
  * `energy::Float32`: クラスターのエネルギー [GeV]
  * `energyError::Float32`: エネルギーの誤差
  * `position::Vector3f`: クラスターの位置 [mm]
  * `positionError::SVector{6,Float32}`: 位置の共分散行列 (6パラメータ)
  * `iTheta::Float32`: 位置Thetaでのクラスターの内因的方向。IPから見たクラスターの方向と混同しないでください。
  * `phi::Float32`: 位置- Phiでのクラスターの内因的方向。IPから見たクラスターの方向と混同しないでください。
  * `directionError::Vector3f`: 方向の共分散行列 (3パラメータ) [mm^2]
  * `shapeParameters::PVector{Float32}`: 形状パラメータ - サイズとパラメータの名前については、コレクションパラメータClusterShapeParametersを確認/設定してください。
  * `subdetectorEnergies::PVector{Float32}`: 特定のサブデテクターで観測されたエネルギー。配列のインデックスをデコードするために、コレクションパラメータClusterSubdetectorNamesを確認/設定してください。

# 関係

  * `clusters::Cluster`: このクラスターに結合されたクラスター。
  * `hits::CalorimeterHit`: このクラスターに結合されたヒット。
  * `particleIDs::ParticleID`: 粒子ID（その可能性に基づいてソート）

# メソッド

  * `setShapeParameters(object::Cluster, v::AbstractVector{Float32})`: `shapeParameters`ベクターメンバーに値のセットを割り当てる
  * `setSubdetectorEnergies(object::Cluster, v::AbstractVector{Float32})`: `subdetectorEnergies`ベクターメンバーに値のセットを割り当てる
  * `pushToClusters(obj::Cluster, robj::Cluster)`: 関連オブジェクトを`clusters`関係にプッシュする
  * `popFromClusters(obj::Cluster)`: `clusters`関係から最後の関連オブジェクトをポップする
  * `pushToHits(obj::Cluster, robj::CalorimeterHit)`: 関連オブジェクトを`hits`関係にプッシュする
  * `popFromHits(obj::Cluster)`: `hits`関係から最後の関連オブジェクトをポップする
  * `pushToParticleIDs(obj::Cluster, robj::ParticleID)`: 関連オブジェクトを`particleIDs`関係にプッシュする
  * `popFromParticleIDs(obj::Cluster)`: `particleIDs`関係から最後の関連オブジェクトをポップする
