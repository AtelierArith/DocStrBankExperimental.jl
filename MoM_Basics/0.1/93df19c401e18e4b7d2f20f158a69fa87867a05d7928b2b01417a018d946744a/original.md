```
SimulationParamsType
```

非数值仿真参数信息：

```
resultDir   ::String        结果文件夹路径
ieT         ::Symbol        积分方程类型，包括 EFIE, MFIE, CFIE等
meshfilename::String        网格文件名称
meshunit    ::Symbol        网格文件单位
SHOWIMAGE   ::Bool          根是否要在前端显示图片
discreteVar ::String        离散的体未知量类型，支持位移电流 `"D"` 或等效电流 `"J"`
sbfT        ::Symbol        面基函数类型，目前仅支持 `:RWG`
vbfT        ::Symbol        体基函数类型，目前支持 `:SWG, :RBF, :PWC`
recordMem   ::Bool          是否记录内存信息
```
