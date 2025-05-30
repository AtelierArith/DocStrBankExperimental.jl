レシピ内で使用され、追加の RecipeData オブジェクトをリストに追加するためのものです：

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

    # これはメインの系列です... 何も返さないことでスキップできます。
    # 注：@series ブロックは何も返しません
    rand(100)
end
```
