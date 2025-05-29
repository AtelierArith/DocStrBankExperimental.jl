```
struct TextFormat
```

# フィールド

  * `up_right_corner::Char`: 右上隅の文字。
  * `up_left_corner::Char`: 左上隅の文字。
  * `bottom_left_corner::Char`: 左下隅の文字。
  * `bottom_right_corner::Char`: 右下隅の文字。
  * `up_intersection::Char`: 上部の線の交差点にある文字。
  * `left_intersection::Char`: 左部の線の交差点にある文字。
  * `right_intersection::Char`: 右部の線の交差点にある文字。
  * `middle_intersection::Char`: テーブルの中央の線の交差点にある文字。
  * `bottom_intersection::Char`: 下部の線の交差点にある文字。
  * `column::Char`: テーブル内の縦の線にある文字。
  * `row::Char`: テーブル内の横の線にある文字。
  * `hlines::Vector{Symbol}`: デフォルトで描画されるべき水平線。
  * `vlines::Union{Symbol, Vector{Symbol}}`: デフォルトで描画されるべき垂直線。

# 事前定義されたフォーマット

以下の事前定義されたフォーマットが利用可能です: `unicode` (**デフォルト**), `mysql`, `compact`, `markdown`, `simple`, `ascii_rounded`, および `ascii_dots`。
