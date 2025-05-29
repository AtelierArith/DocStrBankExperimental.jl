```
convex_hull(points::Vector{VN}; [algorithm]=nothing, [backend]=nothing,
            [solver]=nothing) where {N, VN<:AbstractVector{N}}
```

点のリストの凸包を計算します。

### 入力

  * `points`    – 点のリスト
  * `algorithm` – （オプション、デフォルト: `nothing`）凸包アルゴリズム; 有効なオプションについては下記を参照
  * `backend`   – （オプション、デフォルト: `nothing`）高次元点集合のための多面体計算バックエンド
  * `solver`    – （オプション、デフォルト: `nothing`）バックエンドで使用される線形計画ソルバー

### 出力

点のリストとしての凸包。

### アルゴリズム

前処理ステップでは、1次元の場合は最大2点、2次元の場合は最大4点のケースを処理します。1次元または2次元でより多くの点がある場合は、より一般的なアルゴリズムを使用します。

1次元の場合、最小点と最大点をその順序で返します。

2次元の場合は、平面凸包アルゴリズムを使用して処理します。以下のアルゴリズムが利用可能です：

  * `"monotone_chain"`        – アンドリューの単調チェーン法を使用して平面上の点の凸包を計算
  * `"monotone_chain_sorted"` – `"monotone_chain"`と同じですが、点がすでに反時計回りにソートされていると仮定

詳細については、それぞれのアルゴリズムの参照ドキュメントを参照してください。

高次元の場合は、具体的な多面体ライブラリ`Polyhedra`を使用して処理され、`CDDLib`や`ConvexHull.jl`などのライブラリにアクセスできます。これらのライブラリは`backend`引数を介して選択できます。

### 注意事項

インプレースバージョンを使用する場合は、`convex_hull!`を使用してください。

### 例

ランダムな点のセットの凸包を計算します：

```jldoctest ch_label
julia> points = [randn(2) for i in 1:30]; # 30のランダムな2D点

julia> hull = convex_hull(points);

julia> typeof(hull)
Vector{Vector{Float64}} (alias for Array{Array{Float64, 1}, 1})
```
