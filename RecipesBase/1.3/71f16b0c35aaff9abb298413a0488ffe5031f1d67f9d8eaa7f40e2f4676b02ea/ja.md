レシピ内で追加の RecipeData オブジェクトをリストに追加するために使用されることを意図しています：

```julia
@recipe function f(::T)
    # すべてにこの設定が適用されます
    linecolor --> :red

    @series begin
        # この設定はこの系列のみに適用されます
        fillcolor := :green

        # 引数を返します。レシピと同様です
        rand(10)
    end

    # これはメインの系列です... 何も返さないことでスキップすることもできます。
    # 注：@series ブロックは何も返しません
    rand(100)
end
```
