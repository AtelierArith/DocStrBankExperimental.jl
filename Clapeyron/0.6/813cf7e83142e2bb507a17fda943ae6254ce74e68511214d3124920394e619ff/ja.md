```
function function SPUNG(components,
    refmodel=PropaneRef(),
    shapemodel=SRK(components),
    shaperef = SRK(refmodel.components))
```

## 説明

SPUNG: *天然ガスの利用のための状態研究プログラム*

[`ECS`](@ref) メソッド。形状モデルとして[`SRK`](@ref)を使用し、参照モデルとして[`PropaneRef`](@ref)を使用します。

## 参考文献

1. Wilhelmsen, Ø., Skaugen, G., Jørstad, O., & Li, H. (2012). SPUNG*および炭素捕集と貯蔵モデリングに使用される他の状態方程式の評価。エネルギー手続き、23、236–245。 [doi:10.1016/j.egypro.2012.06.024](https://doi.org/10.1016/j.egypro.2012.06.024)
