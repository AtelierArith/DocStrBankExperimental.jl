```
direct_sum(x::Vararg{TorQuadModule}) -> TorQuadModule, Vector{TorQuadModuleMap}
direct_sum(x::Vector{TorQuadModule}) -> TorQuadModule, Vector{TorQuadModuleMap}
```

トーション二次モジュールのコレクション $T_1, \ldots, T_n$ が与えられたとき、それらの直和 $T := T_1\oplus \ldots \oplus T_n$ と、注入 $T_i \to T$ を返します。

`TorQuadModule` 型のオブジェクトに対して、有限直和と有限直積は一致し、それゆえ双積と呼ばれます。`T` を直積として得たい場合は、射影 $T \to T_i$ を伴って `direct_product(x)` を呼び出すべきです。`T` を双積として得たい場合は、注入 $T_i \to T$ と射影 $T \to T_i$ を伴って `biproduct(x)` を呼び出すべきです。
