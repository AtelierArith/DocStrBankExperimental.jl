```
centroid(geom; gdataset=false)
```

### パラメータ

  * `geom`: ジオメトリ。これはGDAL AbstractGeometryまたはGMTdataset（またはそれらのベクトル）、または行列である可能性があります。

### キーワード

  * `gdataset`: 入力がGMTdatasetまたは行列であってもGDAL IGeometryを返します。

ジオメトリの重心を計算します。

重心は必ずしもジオメトリ内にあるとは限りません。

（このメソッドはSFCOM ISurface::get_Centroid()メソッドに関連していますが、現在の実装はGEOSに基づいており、マルチポイント、ラインストリング、マルチポリゴンなどの他のジオメトリタイプでも動作できます。OGC SF SQL 1.1はサーフェス（ポリゴン）の操作を定義しています。SQL/MM-Part 3はサーフェスとマルチサーフェス（マルチポリゴン）の操作を定義しています。）

### 戻り値

入力が行列またはGMTタイプの場合はGMTデータセット（`gdaset=true`でない限り）、それ以外の場合はGDAL IGeometry。
