```
aircraft
```

TASOPT航空機モデルを表す型で、幾何学的、空力的、推進システムのパラメータを含みます。航空機の名前、説明、および分析と最適化に使用されるさまざまなパラメータセットに関連する情報を保持するように設計されています。

`aircraft`モデルの要約を印刷するためにBase.summaryをオーバーロードします。

# フィールド:

  * `name::String` : 航空機の名前（例: "Boeing 777"）
  * `description::String` : 航空機の簡単な説明
  * `options::TASOPT.Options` : 航空機の構成オプション
  * `parg::AbstractArray{Float64}` : 幾何学的パラメータ
  * `parm::AbstractArray{Float64}` : ミッションパラメータ
  * `para::AbstractArray{Float64}` : 空力パラメータ
  * `pare::AbstractArray{Float64}` : エンジンパラメータ
  * `fuse_tank::fuselage_tank`: 胴体燃料タンクオブジェクト
  * `fuselage::Fuselage`: 胴体オブジェクト
  * `wing::Wing`: 翼オブジェクト
  * `htail::Tail`: 水平尾翼オブジェクト
  * `vtail::Tail`: 垂直尾翼オブジェクト
  * `engine::Engine`: エンジンオブジェクト
  * `landing_gear::LandingGear`: 着陸装置オブジェクト
  * `fuselage::Fuselage` : 胴体のレイアウト、データ、およびパラメータ
  * `fuse_tank::fuselage_tank` : 胴体タンクのデータとパラメータ（該当する場合）
  * `wing::Wing` : 翼のデータとパラメータ
  * `htail::Tail` : 水平尾翼のデータとパラメータ
  * `vtail::Tail` : 垂直尾翼のデータとパラメータ
  * `engine::Engine` : エンジンモデル、データ、およびパラメータ

`par`配列内の特定のデータにアクセスするためのインデックスは`/src/data_structs/index.inc`で定義されています。使用法についてはサンプル入力ファイル（`/example/defaults/default_input.toml`および`read_input.jl`）を参照してください。主要な`struct`の要約についてはドキュメントを参照してください。
