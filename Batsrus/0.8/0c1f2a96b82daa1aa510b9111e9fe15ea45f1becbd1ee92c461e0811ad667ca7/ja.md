```
 readtecdata(file; verbose=false)
```

BATSRUS Tecplot 出力からヘッダー、データ、および接続性を返します。2D および 3D のバイナリおよび ASCII フォーマットの両方がサポートされています。

# 例

```
file = "3d_ascii.dat"
head, data, connectivity = readtecdata(file)
```
