```
@enum LinearDependence INDEPENDENT TRIVIAL DEPENDENT
```

基底の要素の線形依存性は、行のインデックスを表す[`MacaulayNullspace`]に関連しています。`DEPENDENT`は、それが基底の前に現れる行に対して線形依存していることを示します。`TRIVIAL`は、その要素が元の基底に含まれていなかったため、明らかに独立していることを示します。
