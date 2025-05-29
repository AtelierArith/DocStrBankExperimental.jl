Tracker hit plane

  * 著者: Placido Fernandez Declara, CERN

# フィールド

  * `cellID::UInt64`: このヒットを作成したセンサーのID
  * `type::Int32`: 生データヒットのタイプ、edm4hep::RawTimeSeries または edm4hep::SIMTRACKERHIT のいずれか - コレクションパラメータ "TrackerHitTypeNames" と "TrackerHitTypeValues" を参照してください。
  * `quality::Int32`: ヒットの品質ビットフラグ。
  * `time::Float32`: ヒットの時間 [ns]。
  * `eDep::Float32`: ヒットにおけるエネルギーの蓄積 [GeV]。
  * `eDepError::Float32`: EDep に対して測定された誤差 [GeV]。
  * `u::Vector2f`: 測定方向ベクトル、u は x-y 平面にあります
  * `v::Vector2f`: 測定方向ベクトル、v は z に沿っています
  * `du::Float32`: 方向に沿った測定誤差
  * `dv::Float32`: 方向に沿った測定誤差
  * `position::Vector3d`: ヒット位置 [mm]。
  * `covMatrix::SVector{6,Float32}`: 位置 (x,y,z) の共分散、下三角行列として保存されています。すなわち、cov(x,x) , cov(y,x) , cov(y,y) , cov(z,x) , cov(z,y) , cov(z,z)
  * `rawHits::PVector{ObjectID}`: 生データヒット。実際のデータ型を取得するには getType を確認してください。

# メソッド

  * `setRawHits(object::TrackerHitPlane, v::AbstractVector{ObjectID})`: `rawHits` ベクトルメンバーに値のセットを割り当てます
