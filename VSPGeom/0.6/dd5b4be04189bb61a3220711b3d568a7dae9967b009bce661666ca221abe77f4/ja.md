```
VSPComponent(name::String)
```

VSPComponentオブジェクトを定義するパラメータ。

**引数**

  * `name::String`: 名前
  * `type::String`: タイプ
  * `GeomID::String`: ジオメトリID
  * `SurfNdx::Int`: サーフィスインデックス
  * `MainSurfNdx::Int`: メインサーフィスインデックス
  * `SymCopyNdx::Int`: 対称コピーインデックス
  * `surface_node::DataFrame`: サーフェスノードDegenGeom
  * `surface_face::DataFrame`: サーフェスフェイスDegenGeom
  * `plate::DataFrame`: プレートDegenGeom
  * `stick_node::DataFrame`: スティックノードDegenGeom
  * `stick_face::DataFrame`: スティックフェイスDegenGeom
  * `point::DataFrame`: ポイントDegenGeom
