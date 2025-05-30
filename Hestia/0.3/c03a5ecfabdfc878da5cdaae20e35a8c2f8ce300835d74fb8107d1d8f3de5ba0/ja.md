```
DynamicAnisotropic <: AbstractAnisotropicProperty
```

タイプ DynamicAnisotropic は、異方性および温度依存（動的）熱伝導の係数を含みます

$$
    \lambda(\theta) = diag(\lambda_{x}(\theta),\lambda_{y}(\theta),\lambda_{z}(\theta))
$$

### 要素

`λx` : x軸: 熱伝導率係数 

`λy` : y軸: 熱伝導率係数

`λz` : z軸: 熱伝導率係数

`ρ` : 質量密度係数

`c` : 比熱容量係数
