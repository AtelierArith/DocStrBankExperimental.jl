```
sys = parallel(sys1, sys2) 
sys = sys1 + sys2
```

記述子システム `sys1` と `sys2` を並列に接続して `sys = sys1 + sys2` とします。この結合は、それらの伝達関数行列の加算に対応します。行と列の次元が同じ定数行列またはベクトルを持つシステムの並列結合や、UniformScalingsもサポートされています。定数との並列結合は、伝達関数行列を定数で要素ごとに並列に結合することに相当します。
