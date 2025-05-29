モンテカルロ粒子 - lcio::MCParticleに基づく。

  * 著者: F.Gaede, DESY

# フィールド

  * `PDG::Int32`: 粒子のPDGコード
  * `generatorStatus::Int32`: ジェネレーターによって定義された粒子の状態
  * `simulatorStatus::Int32`: シミュレーションプログラムからの粒子の状態 - 以下のBIT定数を使用
  * `charge::Float32`: 粒子の電荷
  * `time::Float32`: イベントに対する粒子の生成時間 [ns]、例えば、事前に割り当てられた崩壊やシミュレーターからの飛行中の崩壊の場合。
  * `mass::Float64`: 粒子の質量 [GeV]
  * `vertex::Vector3d`: 粒子の生成頂点 [mm]。
  * `endpoint::Vector3d`: 粒子の終点 [mm]
  * `momentum::Vector3d`: 生成頂点での粒子の3モーメント [GeV]
  * `momentumAtEndpoint::Vector3d`: 終点での粒子の3モーメント [GeV]
  * `spin::Vector3f`: 粒子のスピン（ヘリシティ）ベクトル。
  * `colorFlow::Vector2i`: ジェネレーターによって定義されたカラー流

# 関係

  * `parents::MCParticle`: この粒子の親。
  * `daughters::MCParticle`: この粒子の娘。

# メソッド

  * `pushToParents(obj::MCParticle, robj::MCParticle)`: 関連オブジェクトを`parents`関係にプッシュ
  * `popFromParents(obj::MCParticle)`: `parents`関係から最後の関連オブジェクトをポップ
  * `pushToDaughters(obj::MCParticle, robj::MCParticle)`: 関連オブジェクトを`daughters`関係にプッシュ
  * `popFromDaughters(obj::MCParticle)`: `daughters`関係から最後の関連オブジェクトをポップ
