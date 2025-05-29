```
subgrid(parent,                                                             
        subregions::AbstractArray;                                          
        transform::T = (a, b) -> a .= b[1:length(a)],
        boundary=false,                                                     
        coordinatesystem=codim1_coordinatesystem(parent[CoordinateSystem]), 
        project=true) where T
```

サブグリッドを領域のリストから作成します。

  * `parent`: 親グリッド
  * `subregions`: サブグリッドを定義するサブリージョンの配列
  * 'support': サブグリッドのサポート、デフォルトは ON*CELLS ですが、ON*FACES または ON_BFACES にすることで、面/境界領域からのコディメンション 1 サブグリッドを作成することもできます
  * `boundary`: true の場合、境界領域からコディメンション 1 サブグリッドを作成します（support = ON_BFACES と同じ）
  * `transform` (kw パラメータ): グリッドとサブグリッドの座標間の変換関数で、1 点に作用します。
  * `coordinatesystem`: `boundary==true` の場合、境界の座標系を指定します。デフォルト: 親の座標系が直交座標系の場合、対応するコディメンション 1 の座標系、そうでない場合: `nothing`、サブグリッドで CellFinder を使用するためにユーザーによる指定が必要です。
  * `project`: 座標をサブグリッドの次元に投影します

サブグリッドは `ExtendableGrid` 型で、2 つの追加コンポーネント [`ParentGrid`](@ref) と [`NodeParents`](@ref) を格納します。
