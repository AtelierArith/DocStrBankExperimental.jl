```
read_nctiles(fileName,fldName,mygrid; I, eccoVersion4Release4=false, verbose=false)
```

NCTilesファイルからモデル出力を読み込み、MeshArrayインスタンスに変換します。キーワード引数`eccoVersion4Release4=true`を設定すると、`read_nctiles`は以前のバージョンとは異なるファイル命名規則を持つECCOv4r4データを読み込むことができます。

```
mygrid=GridSpec("LatLonCap")
fileName="nctiles_grid/GRID"
Depth=read_nctiles(fileName,"Depth",mygrid)
hFacC=read_nctiles(fileName,"hFacC",mygrid)
hFacC=read_nctiles(fileName,"hFacC",mygrid,I=(:,:,1))
```
