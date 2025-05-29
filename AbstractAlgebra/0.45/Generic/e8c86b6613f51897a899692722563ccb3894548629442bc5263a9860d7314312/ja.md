```
localization(R::AbstractAlgebra.Ring, prime::T; cached::Bool=true, comp=false) where {T <: RingElement}
```

リング $R$ の素元 $prime$ によって生成されるイデアルでのリングのローカリゼーションを返します。$R$ はユークリッド整域であり、$prime$ は素元である必要がありますが、どちらもチェックされません。`cached == true`（デフォルト）であれば、結果として得られるローカリゼーション親オブジェクトはキャッシュされ、同じ基底リング $R$ と要素 $prime$ を持つコンストラクタへのその後の呼び出しに対して返されます。
