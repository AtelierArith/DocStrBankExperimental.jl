```
getinterpolatedsolution(nc::NCube{IT,FT,N,Nfc}, mdbm::MDBM_Problem{fcT,N,Nf,Nc,t01T,t11T,IT,FT,aT})
```

提供されたn次元キューブ`nc`内の解の補間された座標を提供します（おおよそfoo(x,y) == 0およびc(x,y)>0の場所）。
