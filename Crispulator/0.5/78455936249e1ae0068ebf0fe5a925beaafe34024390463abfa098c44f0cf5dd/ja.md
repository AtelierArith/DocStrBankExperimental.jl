```julia
transfect(setup, lib, guides, guide_freqs_dist)

```

ライブラリのガイド（`guides`）のトランスフェクションを、[`Crispulator.Library`](@ref) `lib`のパラメータと、カテゴリカル分布`guide_freqs_dist`によって表される頻度に従ってシミュレートします。

この関数は、トランスフェクション後の細胞集団を作成します。各細胞は、ライブラリに存在するガイドの頻度に従って単一のガイドRNAを持っています。その後、細胞は`setup.bottleneck_representation * num_guides`の数になるまで増殖します。FACSスクリーニングでは、細胞の単純な線形増殖を仮定しますが、成長スクリーニングでは、細胞はその表現型とノックダウンの程度に応じて増殖します。
