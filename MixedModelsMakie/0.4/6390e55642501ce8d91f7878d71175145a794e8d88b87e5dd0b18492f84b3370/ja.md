```
qqcaterpillar!(f::Indexable, r::RanefInfo;
               cols::Union{Nothing,AbstractVector}=nothing,
               dotcolor=(:red, 0.2), barcolor=:black)
qqcaterpillar!(f::Indexable, m::MixedModel,
               gf::Symbol=first(fnames(m));
               cols::Union{Nothing,AbstractVector}=nothing,
               dotcolor=(:red, 0.2), barcolor=:black,
               vline_at_zero::Bool=false)
```

正規分布の分位数スケールで縦軸を持つキャタピラープロットで図を更新します。

`MixedModel`を渡すと、`gf`は表示されるグループ化変数を指定します。あるいは、[`ranefinfo`](@ref)を使用して[`RanefInfo`](@ref)オブジェクトを直接構築することもできます。`RanefInfo`を直接構築することで、条件付き分散の再計算を避けることができます。

表示は、`cols`を指定することで、グループ化変数に関連するランダム効果のサブセットに制限できます。これは、インデックスまたは項目名によって指定できます。

縦軸のレベルの順序は、通常は`(Intercept)`ランダム効果の`r.ranef`の`orderby`列に従って増加します。`orderby=nothing`を設定すると、ソートが無効になり、格納されている順序でレベルが返されます。
