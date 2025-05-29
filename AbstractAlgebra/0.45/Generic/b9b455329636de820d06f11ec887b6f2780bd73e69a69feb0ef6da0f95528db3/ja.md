```
 localization(R::AbstractAlgebra.Ring, primes::Vector{T}; cached::Bool=true) where {T <: RingElement}
```

リング $R$ のローカリゼーションを、$primes$ のリング要素によって生成される主イデアルの合併で返します。$R$ はユークリッド整域であり、$primes$ は素元である必要がありますが、どちらもチェックされません。`cached == true`（デフォルト）であれば、結果として得られるローカリゼーション親オブジェクトはキャッシュされ、同じ基底リング $R$ と要素 $primes$ を持つコンストラクタへのその後の呼び出しに対して返されます。
