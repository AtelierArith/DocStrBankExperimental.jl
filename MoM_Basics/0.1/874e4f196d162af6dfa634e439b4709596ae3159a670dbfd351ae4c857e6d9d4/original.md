```
AntennaArray{FT<:Real, AT, N} <: AbstractAntennaArray
```

机扫阵列天线 (mechanically scanned array, MSA)、相控阵 (Phased Array)阵列天线 orient 采用的是欧拉角，参考[`eulerRotationMat`](@ref) 注意阵列初始指向由提供的天线单元合成，作为阵列只提供指向旋转。
