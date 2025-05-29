```
 trace(fieldx, fieldy, fieldz, startx, starty, startz, gridx, gridy, gridz;
	 alg=RK4(), kwargs...)

 trace(fieldx, fieldy, fieldz, startx, starty, startz, grid::CartesianGrid;
	 alg=RK4(), maxstep=20000, ds=0.01, gridtype="ndgrid", direction="both")
```

3D配列のフィールドと範囲内のグリッドを持つ構造化メッシュでのストリームトレース。
