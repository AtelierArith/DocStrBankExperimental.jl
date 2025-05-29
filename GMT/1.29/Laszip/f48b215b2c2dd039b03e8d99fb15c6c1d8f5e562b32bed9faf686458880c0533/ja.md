```
lazwrite(FileName::AbstractString, xyz; grd_hdr=[], scaleX=nothing, scaleY=nothing, scaleZ=nothing, offX=nothing, offY=nothing, offZ=nothing)
```

XYZデータをLIDAR laz（laszip圧縮）またはlas形式のファイルに書き込みます。

```
ここで：
	"FileName" 出力LIDARファイルの名前
	xyz  ポイント座標を持つMx3配列
```

### 例

x,y,zデータをファイル"lixo.laz"に書き込むには、次のようにします：

```julia
	lazwrite("lixo.laz", xyz)
```
