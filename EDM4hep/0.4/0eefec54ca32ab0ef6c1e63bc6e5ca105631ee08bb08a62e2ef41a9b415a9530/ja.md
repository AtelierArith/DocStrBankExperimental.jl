再構築されたトラック

  * 著者: F.Gaede, DESY

# フィールド

  * `type::Int32`: トラックのタイプを定義するフラグワード。ビット16-31は内部で使用される
  * `chi2::Float32`: トラックフィットのカイ二乗
  * `ndf::Int32`: トラックフィットの自由度の数
  * `dEdx::Float32`: トラックのdEdx。
  * `dEdxError::Float32`: dEdxの誤差。
  * `radiusOfInnermostHit::Float32`: トラックフィットに使用された最も内側のヒットの半径
  * `subdetectorHitNumbers::PVector{Int32}`: 特定のサブデテクターにおけるヒットの数。インデックスをデコードするためのコレクション変数TrackSubdetectorNamesを確認/設定
  * `trackStates::PVector{TrackState}`: トラックの状態
  * `dxQuantities::PVector{Quantity}`: dx量の異なる測定値

# 関係

  * `trackerHits::TrackerHit`: このトラックを作成するために使用されたヒット
  * `tracks::Track`: このトラックを作成するために結合されたトラック（セグメント）

# メソッド

  * `setSubdetectorHitNumbers(object::Track, v::AbstractVector{Int32})`: `subdetectorHitNumbers`ベクターメンバーに値のセットを割り当てる
  * `setTrackStates(object::Track, v::AbstractVector{TrackState})`: `trackStates`ベクターメンバーに値のセットを割り当てる
  * `setDxQuantities(object::Track, v::AbstractVector{Quantity})`: `dxQuantities`ベクターメンバーに値のセットを割り当てる
  * `pushToTrackerHits(obj::Track, robj::TrackerHit)`: 関連オブジェクトを`trackerHits`関係にプッシュする
  * `popFromTrackerHits(obj::Track)`: `trackerHits`関係から最後の関連オブジェクトをポップする
  * `pushToTracks(obj::Track, robj::Track)`: 関連オブジェクトを`tracks`関係にプッシュする
  * `popFromTracks(obj::Track)`: `tracks`関係から最後の関連オブジェクトをポップする
