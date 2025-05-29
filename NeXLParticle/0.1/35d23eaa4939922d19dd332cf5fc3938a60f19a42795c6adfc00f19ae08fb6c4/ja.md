```
signature( #
    sig::Signature,
    krs::Vector{KRatio},
    special::Set{Element},
    drop::Set{Element}
)::Dict{Element,Float64}
```

指定された k-ratio のセットから「粒子シグネチャ」を計算します。粒子シグネチャは、純粋な元素に対する正規化された k-ratio に似ていますが、1) 特定の元素を正規化から除外することができ、2) これらの元素を非正規化として結果に含めることができます。
