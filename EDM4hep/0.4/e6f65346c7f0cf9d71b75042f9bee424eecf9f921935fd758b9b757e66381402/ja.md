カロリメーターヒット

  * 著者: F.Gaede, DESY

# フィールド

  * `cellID::UInt64`: 検出器特有の（幾何学的な）セルID。
  * `energy::Float32`: ヒットのエネルギー [GeV]。
  * `energyError::Float32`: ヒットエネルギーの誤差 [GeV]。
  * `time::Float32`: ヒットの時間 [ns]。
  * `position::Vector3f`: ヒットの位置（ワールド座標系） [mm]。
  * `type::Int32`: ヒットのタイプ。整数タイプを名前にマッピングするためのコレクションパラメータ "CalorimeterHitTypeNames" と "CalorimeterHitTypeValues"。
