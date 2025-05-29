```
setsrs!(GID::Union{GItype, GDtype}; prj::String="", proj::String="", proj4::String="", wkt::String="", epsg::Int=0)
```

または

```
setcrs!(GID::Union{GItype, GDtype}; prj::String="", proj::String="", proj4::String="", wkt::String="", epsg::Int=0)
```

GMTgrid、GMTimage、またはGMTdataset(s)の空間参照を設定します。グリッド/画像/データセットオブジェクトを参照する方法を1つ以上渡します。複数の方法を渡す場合、残りの情報は冗長であり、矛盾してはいけません。

  * `prj`、`proj`、または`proj4`: PROJ4文字列を渡すためのエイリアス。
  * `wkt`: WKT（Well Known Format）文字列。
  * `epsg`: EPSGコード。

### 戻り値

この関数は何も返しません。実行することはオブジェクトの参照情報を追加/変更することです。
