```
ExtendedCorrespondingStates <: EoSModel

function ECS(components,
    refmodel=PropaneRef(),
    shapemodel=SRK(components),
    shaperef = SRK(refmodel.components))
```

## 入力モデル

  * `shape_model`: 形状モデル
  * `shape_ref`: 形状参照。`shape_model`と同じタイプのEoS
  * `model_ref`: 参照モデル

## 説明

拡張対応状態法。

アイデアは、対応状態パラメータを提供する「形状モデル」と、ヘルムホルツエネルギー関数を実装する「参照モデル」を使用することです。これにより：

```
eos(shape_model,v,T,x)/RT = eos(model_ref,v₀,T₀)/RT₀
```

ここで：

```
T₀ = T/f
v₀ = v/h
f,h = shape_factors(model::ECS,shape_ref::EoSModel,V,T,z)
```

[`shape_factors`](@ref)は、カスタム拡張対応状態モデルを作成するために使用できます。

## 参考文献

.1 Mollerup, J. (1998). 二パラメータ状態方程式の統一と対応状態の原理。流体相平衡、148(1–2)、1–19。 [doi:10.1016/s0378-3812(98)00230-1](https://doi.org/10.1016/s0378-3812(98)00230-1)
