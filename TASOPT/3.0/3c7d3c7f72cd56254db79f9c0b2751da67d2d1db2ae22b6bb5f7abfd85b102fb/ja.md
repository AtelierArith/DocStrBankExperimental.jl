```
PayloadRange(ac_og, Rpts, Ppts, filename, OEW, itermax)
```

航空機のペイロード範囲図をプロットするための関数

!!! details "🔃 入力と出力"
    **入力:**

      * `ac_og::aircraft`: ペイロード範囲図のための航空機構造。
      * `Rpts::Int64`: プロットする範囲の密度（オプション）。
      * `Ppts::Int64`: プロットするペイロードの密度（オプション）。
      * `filename::String`: プロットを保存するためのファイル名文字列（オプション）。
      * `OEW::Bool`: y軸にOEW+ペイロードを表示するか、単にペイロードを表示するか（オプション）。
      * `itermax::Int64`: fly_mission! ループの最大反復回数（オプション）。
      * `initializes_engine::Boolean`: trueの場合、エンジン状態の初期推測として設計ケースを使用（オプション）。
      * `Ldebug::Bool`: 冗長性フラグ。デフォルトはfalseで、PRスイープの進行に伴い出力を隠す（オプション）。

