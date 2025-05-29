```
interpolate!(mdbm::MDBM_Problem{fcT,N,Nf,Nc,t01T,t11T,IT,FT,aT}; interpolationorder::Int=1)
```

n-立方体内で解を補間し、`interpolationorder`の順序を指定します。

  * `interpolationorder=0` はn-立方体の中点を提供します
  * `interpolationorder=1` は線形フィットを行い、n-立方体の中点に最も近い解の点を提供します
