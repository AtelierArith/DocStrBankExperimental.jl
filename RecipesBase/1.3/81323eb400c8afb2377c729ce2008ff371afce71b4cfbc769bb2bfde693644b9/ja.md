自分のプロットレシピを便利なメソッドで簡単に定義できます：

```julia
@userplot GroupHist

@recipe function f(gh::GroupHist)
    # 一部の属性を設定し、gh.argsを入力として使用していくつかの系列を追加します
end
# これで次のようにプロットできます：
grouphist(rand(1_000, 4))
```
