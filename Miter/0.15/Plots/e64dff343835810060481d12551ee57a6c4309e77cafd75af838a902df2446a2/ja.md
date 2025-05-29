```julia
Tableau(contents; horizontal_divisions, vertical_divisions)

```

*tableau*を作成します。これは、行列のようなグリッド上にプロットを配置したものです。視覚的には、この配置はJuliaが行列を表示する方法に対応しています：行は行として、列は列としてレンダリングされます。

ベクトルを配置するには、[`balanced_matrix`](@ref)を参照してください。

軸は自動的に整列されません。[`sync_bounds`](@ref)を使用してください。

# 分割

FIXME 分割構文の使い方を説明する

# サポートされているAPI

`contents`は、配列インターフェースを介して行列として公開されています。

`Tableau`を`hcat`、`vcat`、および`hvcat`（`[...] ; ...`）でマージできます。
