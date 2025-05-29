```
kDataCart(acqData::AcquisitionData)
```

`acqData`に含まれる直交k空間をすべての`echo`、`coil`、`slice`および`rep`（繰り返し）について返します。次元は：[x,y,z*slices,channels,echoes,repetitions]です。
