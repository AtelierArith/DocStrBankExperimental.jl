```julia
subgrid(
    parent,
    subregions::AbstractArray;
    transform,
    boundary,
    project
) -> ExtendableGrids.ExtendableGrid

```

領域のリストからサブグリッドを作成します。

  * `parent`: 親グリッド
  * `subregions`: サブリージョンの配列
  * `transform` (kw パラメータ): グリッドとサブグリッドの座標間の変換関数で、1つの点に作用します。デフォルト: `copytransform`
  * `boundary`: true の場合、境界領域からコディメンション 1 のサブグリッドを作成します。
  * `project`: 座標をサブグリッドの次元に投影します。

サブグリッドは `ExtendableGrid` 型で、2つの追加コンポーネント [`ParentGrid`](@ref) と [`NodeInParent`](@ref) を格納します。
