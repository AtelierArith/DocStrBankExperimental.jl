```
is_primary(T::TorQuadModule, p::Union{Integer, ZZRingElem}) -> Bool
```

トーション二次モジュール `T` と素数 `p` が与えられたとき、`T` の基礎となる（有限の）アーベル群（[`abelian_group`](@ref）を参照）が `p`-群であるかどうかを返します。
