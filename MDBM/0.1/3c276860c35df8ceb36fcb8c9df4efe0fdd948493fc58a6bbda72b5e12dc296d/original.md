```
getinterpolatedsolution(nc::NCube{IT,FT,N,Nfc}, mdbm::MDBM_Problem{fcT,N,Nf,Nc,t01T,t11T,IT,FT,aT})
```

Provide the interpolated coordinates of the solution inside the provided n-cube `nc` (approximately where foo(x,y) == 0 and c(x,y)>0).
