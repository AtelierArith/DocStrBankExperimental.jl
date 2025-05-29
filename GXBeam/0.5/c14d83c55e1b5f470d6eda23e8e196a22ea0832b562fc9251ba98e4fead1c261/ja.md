```
strain_recovery(F, M, nodes, elements, cache; gxbeam_order=true)
```

各要素の断面における応力とひずみを計算します。

# 引数

  * `F::Vector(3)`: この断面におけるx、y、z方向の力
  * `M::Vector(3)`: この断面におけるx、y、z方向のモーメント
  * `nodes::Vector{Node{TF}}`: メッシュ内のすべてのノード
  * `elements::Vector{MeshElement{TF}}`: メッシュ内のすべての要素
  * `cache::SectionCache`: これにより、コンプライアンス解法からデータを再利用する必要があります（したがって、キャッシュを初期化し、コンプライアンスとこの関数の両方に渡す必要があります）

# キーワード引数

  * `gxbeam_order=true::Bool`: trueの場合、`F`と`M`はGXBeamによって使用されるローカルビーム軸に沿っていると仮定されます（ビームがx軸に沿って延びる場合）。これにより、GXBeamによって設定された軸の順序でビームの応力とひずみも返されます（例：軸方向の応力は`xx`方向、または最初のインデックスに対応します）。

# 戻り値

  * `strain_b::Vector(6, ne)`: 各要素のビーム座標系におけるひずみ。順序: xx, yy, zz, xy, xz, yz   注: この順序（および以下の順序）は、`gxbeam_order`が`true`に設定されている場合、ローカルビーム参照フレームに対応します。
  * `stress_b::Vector(6, ne)`: 各要素のビーム座標系における応力。順序: xx, yy, zz, xy, xz, yz
  * `strain_p::Vector(6, ne)`: 各要素のプライ座標系におけるひずみ。順序: 11, 22, 33, 12, 13, 23
  * `stress_p::Vector(6, ne)`: 各要素のプライ座標系における応力。順序: 11, 22, 33, 12, 13, 23
