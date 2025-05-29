```
TensorValue{D1,D2,T,L} <: MultiValue{Tuple{D1,D2},T,2,L}
```

Type representing a second-order `D1`×`D2` tensor. It must hold `L` = `D1`*`D2`.

If only `D1` or no dimension parameter is given to the constructor, `D1`=`D2` is assumed.
