再構成されたイオン化クラスター

  * 著者: Wenxing Fang, IHEP

# フィールド

  * `cellID::UInt64`: セルID。
  * `significance::Float32`: 有意性。
  * `type::Int16`: タイプ。

# 関係

  * `trackerPulse::TrackerPulse`: イオン化クラスターを作成するために使用されるTrackerPulse。

# メソッド

  * `pushToTrackerPulse(obj::RecIonizationCluster, robj::TrackerPulse)`: 関連オブジェクトを`trackerPulse`関係にプッシュする
  * `popFromTrackerPulse(obj::RecIonizationCluster)`: `trackerPulse`関係から最後の関連オブジェクトをポップする
