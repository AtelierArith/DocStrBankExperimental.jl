```
getinterpolatedsolution(ncubes::Vector{<:NCube},mdbm::MDBM_Problem{N,Nf,Nc})
```

選択されたn-キューブの検出された解の補間された座標を提供します（おおよそfoo(x,y) == 0およびc(x,y)>0の場所）。
