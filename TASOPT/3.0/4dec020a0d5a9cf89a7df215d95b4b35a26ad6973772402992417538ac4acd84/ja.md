```
fly_mission!(ac, imission, itermax, initializes_engine)
```

指定されたミッションを通じて航空機を運行し、燃料重量を計算して収束させます。以前は `fly_offdesign_mission!()` でした。

!!! details "🔃 入力と出力"



**入力:**

  * `ac::aircraft`: 最初のミッションが設計ミッションである航空機
  * `imission::Int64`: 実行するオフデザインミッション (デフォルト: 1)
  * `itermax::Int64`: サイズ決定ループの最大反復回数
  * `initializes_engine::Boolean`: true の場合、設計ケースをエンジン状態の初期推定として使用

**出力:**

  * 明示的な出力はありません。計算された量は、選択されたミッションのために `aircraft` モデルの `par` 配列に保存されます。
