```
biproduct(x::Vararg{T}) where T <: AbstractSpace -> T, Vector{AbstractSpaceMor}, Vector{AbstractSpaceMor}
biproduct(x::Vector{T}) where T <: AbstractSpace -> T, Vector{AbstractSpaceMor}, Vector{AbstractSpaceMor}
```

与えられた二次元またはエルミート空間のコレクション $V_1, \ldots, V_n$ に対して、それらのバイプロダクト $V := V_1 \oplus \ldots \oplus V_n$ を返し、注入 $V_i \to V$ と射影 $V \to V_i$ を返します。

`AbstractSpace` 型のオブジェクトの場合、有限直和と有限直積は一致し、それらはバイプロダクトと呼ばれます。注入 $V_i \to V$ を伴う直和として `V` を取得したい場合は、`direct_sum(x)` を呼び出す必要があります。射影 $V \to V_i$ を伴う直積として `V` を取得したい場合は、`direct_product(x)` を呼び出す必要があります。
