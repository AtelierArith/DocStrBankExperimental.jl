```
struct Rounded{T <: Coordinate} <: GeometryEntityStyle
    abs_r::T = zero(T)
    rel_r::Float64 = 0.0
    min_side_len::T = r
    min_angle::Float64 = 1e-3
    p0::Vector{Point{T}} = []
    inverse_selection::Bool = false
end
```

絶対半径 `abs_r` または相対半径 `rel_r` によって定義される丸みのあるポリゴンスタイル。`abs_r` または `rel_r` のいずれか一方だけが非ゼロであることができます。内部カットを持つ形状や、セグメントの長さに対して角度が鋭すぎる形状には対応できません。`rel_r` が非ゼロの場合、各頂点での曲率半径は `rel_r * min(l₁, l₂)` で計算され、ここで `l₁` と `l₂` は接続された2つの線分の長さを示します。

使用例:

```julia
r = Rectangle(10μm, 10μm)
rsty = Rounded(1μm)
# 様々な構文オプションを持つ丸みのある長方形 StyledEntity を作成
rounded_rect = rsty(r)
rounded_rect = styled(r, rsty)
rounded_rect = Rounded(r, 1μm)
# 結果を通常のポリゴンに変換
rounded_rect_discretized_poly = to_polygons(rounded_rect)
```

## キーワード引数

  * `min_side_len`: 丸められる最小辺の長さ（例：90度の角度の場合、`min_side_len = 2 * rounding_radius` とするのが理にかなっています）。これは現在、正確な比較を使用しているため、非常に短い直線エッジが生成されたり、浮動小数点の不正確さにより角を丸められないことがあります。
  * `min_angle`: 隣接する辺が `min_angle` で設定された許容範囲内で共線の場合、丸めは行われません。
  * `p0`: ポリゴンに適用されたときに丸めを試みる頂点を選択するために使用されるターゲットポイントのセット。`min_side_len` と `min_angle` が満たされる選択された頂点は丸められます。空の場合、すべての頂点が選択されます。それ以外の場合、`p0` の各点に対して、スタイル付きポリゴン内の最も近い点が選択されます。`ClippedPolygon` の場合、同じ `p0` がすべての輪郭に使用されることに注意してください。異なる輪郭に異なる丸めスタイルを使用するには、`StyleDict` を使用してください。
  * `inverse_selection`: true の場合、`p0` からの選択が反転されます。つまり、`p0` によって選択された角を除いて、すべての角が丸められます。
