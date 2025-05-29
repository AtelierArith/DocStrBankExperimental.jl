```
polygonize(geom; gdataset=false)
```

### パラメータ

  * `geom`: ジオメトリ。これはGDAL AbstractGeometryまたはGMTdataset（またはそのベクトル）、または行列であることができます。
  * `gdataset`: 入力がGMTdatasetまたは行列であってもGDAL IGeometryを返します。

スパースエッジのセットをポリゴン化します。

新しいジオメトリオブジェクトが作成され、再構成されたポリゴンのコレクションを含むものが返されます：入力コレクションがMultiLinestringに対応しない場合、またはエッジをポリゴンに再構成することがトポロジーの不整合のために不可能な場合はNULLが返されます。

### 戻り値

入力が行列またはGMTタイプの場合はGMTデータセット（`gdaset=true`でない限り）、それ以外の場合はGDAL IGeometry。
