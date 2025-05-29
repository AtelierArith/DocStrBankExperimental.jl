```
interpolate!(mdbm::MDBM_Problem{fcT,N,Nf,Nc,t01T,t11T,IT,FT,aT}; interpolationorder::Int=1)
```

Interpolate the solution within the n-cube with order `interpolationorder`.

  * `interpolationorder=0` provide the midpoint of the n-cube
  * `interpolationorder=1` preform a linear fit and provide closest solution point to the mindpoint of the n-cube
