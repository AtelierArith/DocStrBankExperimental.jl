```
qqcaterpillar(m::MixedModel, gf::Symbol=first(fnames(m));
              kwargs...)
```

ランダム効果の平均と予測区間の「qq-キャタピラー プロット」の `Figure` を返します。

`gf` は表示されるグループ化変数を指定します。

`kwargs...` は [`qqcaterpillar!`](@ref) に渡されます。
