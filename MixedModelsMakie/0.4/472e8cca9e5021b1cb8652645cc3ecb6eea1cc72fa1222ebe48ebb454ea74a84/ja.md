```
caterpillar(m::MixedModel, gf::Symbol; kwargs...)
```

ランダム効果の平均と予測区間の「キャタピラープロット」の `Figure` を返します。

「キャタピラープロット」は、ランダム効果の条件付き平均と標準偏差の水平誤差棒プロットです。

`gf` は表示されるグルーピング変数を指定します。

`kwargs...` は [`caterpillar!`](@ref) に渡されます。
