```
direct_sum(x::Vararg{T}) where T <: AbstractSpace -> T, Vector{AbstractSpaceMor}
direct_sum(x::Vector{T}) where T <: AbstractSpace -> T, Vector{AbstractSpaceMor}
```

与えられた二次元またはエルミート空間のコレクション $V_1, \ldots, V_n$ に対して、それらの直和 $V := V_1 \oplus \ldots \oplus V_n$ を返し、注入 $V_i \to V$ を提供します。

`AbstractSpace` 型のオブジェクトに対して、有限直和と有限直積は一致し、それらは双積と呼ばれます。もし `V` を直積として得たい場合は、射影 $V \to V_i$ を伴って `direct_product(x)` を呼び出すべきです。もし `V` を双積として得たい場合は、注入 $V_i \to V$ と射影 $V \to V_i$ を伴って `biproduct(x)` を呼び出すべきです。
