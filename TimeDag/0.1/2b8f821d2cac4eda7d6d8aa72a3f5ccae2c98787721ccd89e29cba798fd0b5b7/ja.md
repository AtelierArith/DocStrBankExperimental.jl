```
convert_value(T, x::Node[; upcast=false]) -> Node
```

ノード `x` の値を型 `T` に変換します。

結果のノードの値の型は、`upcast=true` の場合に限り `T` であることが保証されます。詳細はノートで説明します。

!!! note
    デフォルトでは、`convert_value` は `Base.convert` と似た意味を持ち、返されるノードの [`value_type`](@ref) は `T` のサブタイプである可能性があります。

    具体的な例：

    ```jldoctest
    julia> x = convert_value(Any, constant("hello"));

    julia> value_type(x)
    String
    ```

    同じことが `convert(Any, "hello")` を呼び出した場合にも起こります。

    しかし、`upcast=true` に設定すると：

    ```jldoctest
    julia> x = convert_value(Any, constant("hello"); upcast=true);

    julia> value_type(x)
    Any
    ```

