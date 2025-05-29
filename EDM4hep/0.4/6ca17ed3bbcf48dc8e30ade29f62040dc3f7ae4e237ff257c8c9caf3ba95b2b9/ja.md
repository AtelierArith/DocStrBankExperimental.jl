Tracker hit

  * 著者: F.Gaede, DESY

# フィールド

  * `cellID::UInt64`: このヒットを作成したセンサーのID
  * `type::Int32`: 生データヒットのタイプ、edm4hep::RawTimeSeries または edm4hep::SIMTRACKERHIT のいずれか - コレクションパラメータ "TrackerHitTypeNames" と "TrackerHitTypeValues" を参照してください。
  * `quality::Int32`: ヒットの品質ビットフラグ。
  * `time::Float32`: ヒットの時間 [ns]。
  * `eDep::Float32`: ヒットにおけるエネルギーの蓄積 [GeV]。
  * `eDepError::Float32`: EDepで測定された誤差 [GeV]。
  * `position::Vector3d`: ヒット位置 [mm]。
  * `covMatrix::SVector{6,Float32}`: 位置 (x,y,z) の共分散、下三角行列として保存されています。すなわち、cov(x,x) , cov(y,x) , cov(y,y) , cov(z,x) , cov(z,y) , cov(z,z)
  * `rawHits::PVector{ObjectID}`: 生データヒット。実際のデータ型を取得するには getType を確認してください。

# メソッド

  * `setRawHits(object::TrackerHit, v::AbstractVector{ObjectID})`: `rawHits` ベクターメンバーに値のセットを割り当てる
