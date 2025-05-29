```
distribloads(
    self::FEMM,
    assembler::A,
    geom::NodalField{FT},
    P::NodalField{T},
    fi::ForceIntensity,
    m,
) where {FEMM<:AbstractFEMM, A<:AbstractSysvecAssembler, FT<:Number, T}
```

分布荷重ベクトルを計算します。

# 引数

  * `fi`=力の強度オブジェクト
  * `m`= 多様体の次元、0= 頂点（点）、1= 曲線、2= 表面、3= 体積。体荷重の場合、`m`は3に設定され、表面のトラクションの場合は2に設定されます。

実際の作業は`linform_dot()`によって行われます。
