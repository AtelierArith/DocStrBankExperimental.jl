```
shape_factors(model::ECS,V,T,z=SA[1.0])
shape_factors(model::ECS,shape_ref::ABCubicModel,V,T,z=SA[1.0])
shape_factors(model::ECS,shape_ref::EoSModel,V,T,z=SA[1.0])
```

`f` および `h` スケーリングファクターを返します。これは [`ECS`](@ref) 状態方程式で使用されます。

```
eos(shape_model,v,T,x)/RT = eos(model_ref,v₀,T₀)/RT₀
```

ここで：

```
T₀ = T/f
v₀ = v/h
```

立方体の場合、一般的な手順が [1] に定義されています：

```
h = b/b₀
fh = a(T)/a₀(T₀)

```

!!! info "一般的な形状因子？"
    一般的な EoS に関しては、形状因子を取得する方法に関する既存の出版物はありません。しかし、任意の EoS を立方体に「マッピング」することができます：

    ```
    b ≈ lb_volume(model,z)
    a ≈ RT*(b - B)
    B = second_virial_coefficient(model,T)
    ```

    これは広範囲にテストされておらず、今後の変更の対象となる実験的な機能と見なされています。


## 参考文献

1. Mollerup, J. (1998). Unification of the two-parameter equation of state and the principle of corresponding states. Fluid Phase Equilibria, 148(1–2), 1–19. [doi:10.1016/s0378-3812(98)00230-1](https://doi.org/10.1016/s0378-3812(98)00230-1)
