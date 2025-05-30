```
StaticAnisotropic <: AbstractAnisotropicProperty
```

タイプ StaticAnisotropic は、異方性で温度に依存しない（静的）熱伝導の係数を含みます。

$$
    \lambda = diag(\lambda_{x},\lambda_{y},\lambda_{z})
$$

### 要素

`λx` : x軸: 熱伝導率  

`λy` : y軸: 熱伝導率 

`λz` : z軸: 熱伝導率 

`ρ` : 質量密度

`c` : 比熱容量 
