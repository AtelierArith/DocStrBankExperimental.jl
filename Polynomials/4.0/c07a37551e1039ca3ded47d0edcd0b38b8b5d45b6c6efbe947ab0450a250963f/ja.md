```
lowest_terms(pq::AbstractRationalFunction, method=:numerical)
```

`(p,q)`のGCDを見つけ、`u`を返し、`(p÷u)//(q÷u)`を返します。一般的に最小項と呼ばれます。

  * `method`: `gcd(p,q)`に渡されます。
  * `kwargs`: `gcd(p,q)`に渡されます。

デフォルトでは、`AbstractRationalFunction`タイプは共通因子をキャンセルしません。このメソッドは数値的に共通因子をキャンセルし、`q[end]=1`によって正規形に標準化された結果を返します。結果と元のものは有理式としては同等と見なされるかもしれませんが、未定義の関数として見ると異なります。
