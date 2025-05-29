```
renumber!(dh::AbstractDofHandler, order)
renumber!(dh::AbstractDofHandler, ch::ConstraintHandler, order)
```

DofHandlerおよび/またはConstraintHandler内の自由度を、順序`order`に従って再番号付けします。

`order`は次のいずれかのオプションで指定できます：

  * 自由度`i`が`perm[i]`に再番号付けされる順列ベクトル`perm::AbstractVector{Int}`。
  * 自由度をフィールド単位で再番号付けするための[`DofOrder.FieldWise()`](@ref)。
  * 自由度をコンポーネント単位で再番号付けするための[`DofOrder.ComponentWise()`](@ref)。
  * "外部"の再番号付け順列のための`DofOrder.Ext{T}`、詳細については`DofOrder.Ext`のドキュメントを参照してください。

!!! warning
    DofHandlerおよびConstraintHandler内の自由度の番号付けは*常に一貫している必要があります*。したがって、ConstraintHandlerを最初に作成する前に再番号付けするか、DofHandlerとConstraintHandlerを*一緒に*再番号付けする必要があります。

