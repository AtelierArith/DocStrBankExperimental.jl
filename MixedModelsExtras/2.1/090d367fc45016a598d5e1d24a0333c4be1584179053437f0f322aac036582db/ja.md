```
shrinkagenorm(m::MixedModel{T},
              θref::AbstractVector{T}=(isa(m, LinearMixedModel) ? 1e4 : 1) .*
                                      m.optsum.initial;
              uscale=false, p=2)
```

OLS推定値（関連するすべての係数にわたって）から混合モデルのBLUPへの変化のTables.jlテーブルのノルムのNamedTupleを返します。

`p`は$L_p$ノルムに対応し、すなわち$p=2$はユークリッド距離です。

NamedTupleの各エントリは、単一のグルーピング項に対応します。

!!! warning
    この関数は、一時的に渡されたモデルを変更して元の形に戻すため、**スレッドセーフではありません**。

