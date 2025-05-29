```
inputBasicParameters(;frequency::FT = 1e8, ieT::Symbol = :EFIE, CFIEα::FT = 0.6,
meshfilename::String = SimulationParams.meshfilename) where {FT<:AbstractFloat}
```

输入频率参数 `frequency`，修改其它仿真参数的函数； 积分方程类型参数 `ieT`，修改计算过程中采用的积分方程； CFIE混合系数 `CFIEα`、网格文件名 `meshfilename`。
