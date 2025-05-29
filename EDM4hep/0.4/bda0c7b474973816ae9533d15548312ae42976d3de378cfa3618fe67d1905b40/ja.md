シミュレートされたトラッカーヒット

  * 著者: F.Gaede, DESY

# フィールド

  * `cellID::UInt64`: このヒットを生成したセンサーのID
  * `EDep::Float32`: ヒットで放出されたエネルギー [GeV]。
  * `time::Float32`: 実験室系におけるヒットの適切な時間 [ns]。
  * `pathLength::Float32`: このヒットを引き起こした粒子の感度材料内の経路長。
  * `quality::Int32`: 品質ビットフラグ。
  * `position::Vector3d`: ヒット位置 [mm]。
  * `momentum::Vector3f`: ヒット位置における粒子の3次元運動量 [GeV]

# 関係

  * `mcparticle::MCParticle`: ヒットを引き起こしたMCParticle。
