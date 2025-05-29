```
GeometryCanvas{T<:GeometryBasics.Geometry} <: AbstractCanvas

GeometryCanvas{T}(; kw...)
```

Makie.jl `Axis` に GeometryBasics.jl の幾何学を描画するためのキャンバスです。

`T` は `Point`、`LineString` または `Polygon` でなければなりません。

# マウスとキーコマンド

  * 左クリックでポイントを選択するか、`click_property` が設定されている場合はプロパティ 1 を持つポイントを追加します。
  * 右クリックでポイントを選択するか、`click_property` が設定されている場合はプロパティ 2 を持つポイントを追加します。
  * 中クリックでポイントを選択するか、`click_property` が設定されている場合はプロパティ 3 を持つポイントを追加します。
  * Alt+クリック: ポイントを削除し、ドラッグ中にクリックが保持されていると削除を続けます。
  * Shift+クリック: `Polygon` および `LineString` キャンバス上で新しいポリゴンとラインストリングを開始します。`Point` には影響しません。
  * Delete: 選択したポイントを削除します。
  * Shift+Delete: 選択したラインストリング/ポリゴンを削除します。

# キーワード

  * `dragging`: マウスのドラッグを追跡するための Observable{Bool}(false)。
  * `active`: キャンバスがアクティブかどうかを設定するための Observable{Bool}(true)。
  * `accuracy_scale`: 選択の精度を制御します。デフォルトは `1.0` です。
  * `name`: キャンバスの名前のための `Symbol`。[`CanvasSelect`](@ref) に表示されます。
  * `propertynames`: 作成するフィーチャプロパティの名前。
  * `properties`: 既存のプロパティのテーブル。
  * `click_property`: 左クリックと右クリックで設定されるプロパティ、`Bool` である必要があります。
  * `figure`: プロットするためのフィギュア。
  * `axis`: プロットするための軸。
  * `current_point`: 現在フォーカスされているポイントインデックスを追跡するための Observable。
  * `scatter_kw`: `scatter` に渡すキーワード。
  * `lines_kw`: `lines` に渡すキーワード。
  * `poly_kw`: `poly` に渡すキーワード。
  * `current_point_kw`: 現在のポイント `scatter` のためのキーワード。
  * `show_current_point`: 現在のポイントを他のポイントとは異なる方法で表示するかどうか。
  * `text_input`: プロパティ入力のためのテキスト入力ボックスを追加するかどうか。
