```
caterpillar!(f::Indexable, r::RanefInfo;
            orderby=1, cols::Union{Nothing,AbstractVector}=nothing,
            dotcolor=(:red, 0.2), barcolor=:black,
            vline_at_zero::Bool=false)
caterpillar!(f::Indexable, m::MixedModel,
             gf::Symbol=first(fnames(m)); orderby=1,
             cols::Union{Nothing,AbstractVector}=nothing,
             dotcolor=(:red, 0.2), barcolor=:black,
             vline_at_zero::Bool=false)
```

`r` から `f` へのキャタピラープロットの軸を追加します。

`MixedModel` を渡すと、`gf` は表示されるグループ化変数を指定します。あるいは、[`ranefinfo`](@ref) を使用して直接 [`RanefInfo`](@ref) オブジェクトを構築することもできます。`RanefInfo` を直接構築することで、条件付き分散を再計算するのを避けることができます。

垂直軸のレベルの順序は、通常は `(Intercept)` ランダム効果の `r.ranef` の `orderby` 列に従って増加します。`orderby=nothing` に設定すると、ソートが無効になり、格納されている順序でレベルが返されます。

グループ化変数に関連するランダム効果のサブセットに表示を制限するには、`cols` を指定します。インデックスまたは項名で指定できます。

!!! note
    レベルをソートしない場合でも、モデル行列の構築中にすでにソートされている可能性があります。レベルに特定の順序を課したい場合は、`caterpillar!` を呼び出す前に `RanefInfo` オブジェクト内の関連フィールドをソートする必要があります。


!!! note
    `orderby` は、`cols` で指定された列の $n$ 番目の列です。

