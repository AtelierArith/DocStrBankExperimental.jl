```
Matcher(selector; first = false)
```

新しい `Matcher` オブジェクトを作成し、`Node` が `selector` に一致するかどうかをテストするために使用できます。`Matcher` オブジェクトは呼び出し可能で、次のように使用できます。

```julia
function find_first_node(root, selector)
    # `Matcher` オブジェクトを一度作成し、ループ内で再利用します。
    matcher = Matcher(selector)
    for node in AbstractTrees.PreOrderDFS(root)
        if matcher(node)
            return node
        end
    end
    return nothing
end
```

`matcher` オブジェクトには、2つの呼び出し可能なメソッドがあります。最初のメソッドは上記の通り、セレクタが一致するかどうかに応じて `true` または `false` を返します。もう一つのメソッドは、セレクタが一致したときに呼び出される最初の引数関数 `::Node -> Nothing` を取ります。

キーワード引数 `first::Bool` は、`query` によって提供される `first` キーワードと同じ動作をします。詳細については、その関数のドキュメントを参照してください。
