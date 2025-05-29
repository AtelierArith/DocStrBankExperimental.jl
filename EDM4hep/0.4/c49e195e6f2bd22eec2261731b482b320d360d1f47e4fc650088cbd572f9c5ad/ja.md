シミュレートされたカロリメーターヒット

  * 著者: F.Gaede, DESY

# フィールド

  * `cellID::UInt64`: このヒットを生成したセンサーのID
  * `energy::Float32`: ヒットのエネルギー [GeV] 単位。
  * `position::Vector3f`: ヒットの位置をワールド座標系で [mm] 単位で表したもの。

# 関係

  * `contributions::CaloHitContribution`: モンテカルロステップの寄与 - 粒子に平行

# メソッド

  * `pushToContributions(obj::SimCalorimeterHit, robj::CaloHitContribution)`: 関連オブジェクトを `contributions` 関係に追加する
  * `popFromContributions(obj::SimCalorimeterHit)`: `contributions` 関係から最後の関連オブジェクトを削除する
