```
biproduct(x::Vararg{TorQuadModule}) -> TorQuadModule, Vector{TorQuadModuleMap}, Vector{TorQuadModuleMap}
biproduct(x::Vector{TorQuadModule}) -> TorQuadModule, Vector{TorQuadModuleMap}, Vector{TorQuadModuleMap}
```

与えられたトーション二次モジュールのコレクション $T_1, \ldots, T_n$ に対して、それらのバイプロダクト $T := T_1\oplus \ldots \oplus T_n$ を返し、注入 $T_i \to T$ と射影 $T \to T_i$ を返します。

`TorQuadModule` 型のオブジェクトに対して、有限直和と有限直積は一致し、それゆえバイプロダクトと呼ばれます。もし注入 $T_i \to T$ を伴う直和として `T` を得たい場合は、`direct_sum(x)` を呼び出すべきです。もし射影 $T \to T_i$ を伴う直積として `T` を得たい場合は、`direct_product(x)` を呼び出すべきです。
