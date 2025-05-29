```
isgreater(x, y)
```

`isless`の逆ではありません！`x`が`y`より大きいかどうかを、`min`と互換性のある固定の全順序に従ってテストします。

`isless`で定義されているこの関数は通常`isless(y, x)`ですが、`NaN`と[`missing`](@ref)は、通常の値よりも小さいと順序付けられ、`missing`は`NaN`よりも小さいです。

したがって、`isless`は`NaN`と`missing`を最大の値として持つ昇順の全順序を定義し、`isgreater`は`NaN`と`missing`を最小の値として持つ降順の全順序を定義します。

!!! note
    `min`と同様に、`isgreater`はコンテナ（タプル、ベクターなど）を`isless(y, x)`で辞書式に順序付けし、再帰的に自身で順序付けしません：

    ```jldoctest
    julia> Base.isgreater(1, NaN) # 1はNaNより大きい
    true

    julia> Base.isgreater((1,), (NaN,)) # しかし(1,)は(NaN,)より大きくありません
    false

    julia> sort([1, 2, 3, NaN]; lt=Base.isgreater)
    4-element Vector{Float64}:
       3.0
       2.0
       1.0
     NaN

    julia> sort(tuple.([1, 2, 3, NaN]); lt=Base.isgreater)
    4-element Vector{Tuple{Float64}}:
     (NaN,)
     (3.0,)
     (2.0,)
     (1.0,)
    ```


# 実装

これはエクスポートされていません。型は通常この関数を実装すべきではありません。代わりに`isless`を実装してください。
