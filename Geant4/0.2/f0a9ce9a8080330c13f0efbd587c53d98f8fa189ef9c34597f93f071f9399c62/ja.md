```
G4JLApplication(<キーワード引数>)
```

G4JLApplicationをその関連するtyopesおよびメソッドで初期化します。

# 引数

  * `detector::G4JLDetector`: 検出器の説明オブジェクト
  * `simdata=G4JLNoData()`: シミュレーションデータオブジェクト
  * `generator=G4JLParticleGun()`: プライマリ粒子生成器
  * `field=nothing`: 磁場
  * `evtdisplay=nothing`: イベント表示（視覚化）
  * `nthreads=0`: Geant4ワーカースレッドの数（>0はMTを意味します）
  * `verbose=0` : デフォルトの冗長性レベル（物理学など）
  * `runmanager_type=G4RunManager`: 実行マネージャーのタイプ
  * `builder_type=G4JLDetectorConstruction`: 検出器ビルダーのタイプ（デフォルトはほとんどのケースで問題ありません）
  * `physics_type=FTFP_BERT`: 物理リストのタイプ
  * `stepaction_type=G4JLSteppingAction`: ステッピングアクションのタイプ（デフォルトはほとんどのケースで問題ありません）
  * `trackaction_type=G4JLTrackingAction`: トラッキングアクションのタイプ（デフォルトはほとんどのケースで問題ありません）
  * `runaction_type=G4JLRunAction`: 実行アクションのタイプ（デフォルトはほとんどのケースで問題ありません）
  * `eventaction_type=G4JLEventAction`: イベントアクションのタイプ（デフォルトはほとんどのケースで問題ありません）
  * `stepaction_method=nothing`: シグネチャ `(::G4Step, ::G4JLApplication)::Nothing` を持つステッピングアクションメソッド
  * `pretrackaction_method=nothing`: シグネチャ `(::G4Track, ::G4JLApplication)::Nothing` を持つプレトラッキングアクションメソッド
  * `posttrackaction_method=nothing`: シグネチャ `(::G4Track, ::G4JLApplication)::Nothing` を持つポストトラッキングアクションメソッド
  * `beginrunaction_method=nothing`: シグネチャ `(::G4Run, ::G4JLApplication)::Nothing` を持つビギンランアクションメソッド
  * `endrunaction_method=nothing`: シグネチャ `(::G4Run, ::G4JLApplication)::Nothing` を持つエンドランアクションメソッド
  * `begineventaction_method=nothing`: シグネチャ `(::G4Event, ::G4JLApplication)::Nothing` を持つビギンイベントアクションメソッド
  * `endeventaction_method=nothing`: シグネチャ `(::G4Event, ::G4JLApplication)::Nothing` を持つエンドイベントアクションメソッド
  * `stackaction_method=nothing`: シグネチャ `(::G4Track, ::G4JLApplication)::G4ClassificationOfNewTrack` を持つ新しいトラックのスタッキング分類
  * `statechange_method=nothing`: シグネチャ `(from::G4ApplicationState, to::G4ApplicationState, ::G4JLApplication)::Bool` を持つ状態変更通知メソッド
  * `sdetectors::Vector{}=[]`: 論理ボリュームを感度検出器に関連付けるペアのベクター `lv::String => sd::G4JLSensitiveDetector`
  * `scorers::Vector{}=[]`: [`G4JLScoringMesh`](@ref) のベクター
