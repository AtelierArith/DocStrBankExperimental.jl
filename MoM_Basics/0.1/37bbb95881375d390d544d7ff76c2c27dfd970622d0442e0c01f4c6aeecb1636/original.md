```
eulerRotationMat(α::FT, β::FT, γ::FT, unit::Symbol) where{FT<:Real}
```

根据坐标旋转的欧拉角计算旋转矩阵, 定义旋转顺序为： “滚动” → “俯仰” → “偏航”， 即按绕 “z轴” → “x轴” → “z轴”的顺序，分别旋转 α, β, γ 度 [Wikipedia-Euler_angles](https://en.wikipedia.org/wiki/Euler_angles) 输入： α, β, γ, 旋转角度信息 unit: 输入角度值单位，默认为 :rad，可选 :deg 输出： rotMat :: SMatrix{3, 3, FT}, 坐标旋转矩阵 rotMat * vec 将 vec 从局部坐标转换回全局坐标
