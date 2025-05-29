```
BlocksworldRenderer(; options...)
```

[`GraphworldRenderer`](@ref) のブロックワールドドメイン用の特殊化で、カスタム [`BlocksworldLayout`](@ref) とブロックおよびテーブルのデフォルトレンダラーを使用します。以下のブロックワールド特有のオプションがサポートされています：

# オプション

  * `block_type::Symbol`: ブロックのPDDLタイプ、デフォルトは `:block`
  * `block_width::Real`: ブロックの幅、デフォルトは `1.0`
  * `block_height::Real`: ブロックの高さ、デフォルトは `1.0`
  * `block_gap::Real`: ブロック間の隙間、デフォルトは `0.5`
  * `table_height::Real`: テーブルの高さ、デフォルトは `block_height`
  * `gripper_height::Real`: ブロックが持ち上げられたときの高さ。デフォルトは最も高いブロックタワーの少し上です。
  * `block_colors`: ブロックのカラースキーム、デフォルトは `plasma` カラースキームの離散化です。
  * `block_renderer`: ブロックのレンダラー、デフォルトはブロック名が中央に白いテキストで表示されたカラフルな四角形です。
