```
trisurf(in, kw...)
```

3-D三角形サーフェスをプロットします。

三角形分割は、Mx3行列内の点または最初の3列にデータx、y、zを持つGMTdatasetによって定義されます。三角形は内部で行われるDelaunay三角形分割を使用して計算されます。この関数は`plot3d` *アバター*であるため、すべてのオプションは`plot3d`プログラムのものです。

### 例

```julia
    x,y,z = GMT.peaks(N=45, grid=false);
	trisurf([x[:] y[:] z[:]], pen=0.5, show=true)
```
