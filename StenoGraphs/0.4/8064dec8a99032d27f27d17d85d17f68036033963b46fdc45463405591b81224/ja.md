```
@StenoGraph
```

`@StenoGraph`マクロを使用すると、ノードを明示的に宣言することなく参照できます。

```jldoctest
@StenoGraph begin
    # aとbはどこにも宣言されていませんが、`Node(:a)`と`Node(:b)`として機能します
    a → b
end

# 出力

a → b
```

主な欠点は、マクロ内で通常の変数を使用できないことです。もしマクロの外で`c = [Node(:a) Node(:b)]`と宣言しても、内部では`Node(:c)`を参照します。それをエスケープするには[`_`](@ref)を使用する必要があり、つまりマクロ内では`_(c)`として使用します。

エスケープの代替として[`@declage_nodes`](@ref)および[`@declage_nodes_from`](@ref)も参照してください。
