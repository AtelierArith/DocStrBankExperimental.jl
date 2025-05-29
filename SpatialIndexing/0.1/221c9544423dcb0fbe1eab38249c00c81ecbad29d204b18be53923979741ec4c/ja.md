R-Tree: `N`次元空間データインデックス [guttman84].

R-treeはデータ要素（`V`）を葉（`Leaf`）に、葉を枝（`Branch`）にグループ化します。これは、ノード（これらのノードに接続されたデータ要素を含む`Rect{T,N}`矩形）の最小境界矩形（MBR）がコンパクトに保たれ、R-tree階層の同じレベルにあるノードのMBRが互いに最小限の重なりを持つようにするために、さまざまなヒューリスティックを使用します。この特性により、R-treeは空間クエリに対して効率的です。

空間インデックスを容易にするために、`V`データ要素は`HasMBR`トレイトをサポートする必要があります（すなわち、`mbrtype(V)`および`mbr(v::V)`メソッドを定義する必要があります）および、オプションで`HasID`トレイト（`idtype(V)`および`id(v::V)`メソッドを介して）。`mbr(v::V)`は、`v`を含む`Rect{T,N}`型の最小境界矩形（MBR）を返す必要があります。`SpatialElem{T,N,D}`型は、`id`、`mbr`、およびデータオブジェクトの型`D`を明示的に格納し、`HasMBR`および`HasID`トレイトを実装する空間データ要素の一般的な実装を提供します。

# パラメータ

`RTree`の動作は、その作成時に供給されるパラメータによって定義されます：

  * `T`: 空間座標の数値型
  * `N`: 空間次元の数
  * `variant`: `RTreeLinear`、`RTreeQuadratic`、または`RTreeStar`のいずれか（デフォルト）
  * `tight_mbrs`: 子が削除されたときにノードMBRを再計算するかどうか（デフォルトは`true`）
  * `branch_capacity`: 枝ノードの容量（デフォルトは`100`）
  * `leaf_capacity`: 葉ノードの容量（デフォルトは`100`）
  * `leafpool_capacity`: 再利用のために保持すべき切り離された1レベルノード（葉）の数（デフォルトは`100`）
  * `twigpool_capacity`: 再利用のために保持すべき切り離された2レベルノードの数（デフォルトは`100`）
  * `branchpool_capacity`: 再利用のために保持すべき他の（レベル> 2）切り離された枝ノードの数（デフォルトは`100`）
  * `nearmin_overlap`: 最小重なりを持つノードを特定する際に考慮すべき候補の数（デフォルトは`32`）
  * `fill_factor`: 分割後にノードがどれだけ満たされるべきか（その容量の割合）（デフォルトは`0.7`）
  * `split_factor`: 分割後に2つのノードのサイズがどれだけ異なってもよいか（デフォルトは`0.4`）
  * `reinsert_factor`: ノードを削除し、その子を他のノードに再分配することを考慮するために、ノードがどれだけ不足しているべきか（その容量の割合）（デフォルトは`0.3`）

# パフォーマンス

R-treeのノードは、`RTree`作成時に指定された制限された容量（最大子数）を持っています（`leaf_capacity`および`branch_capacity`）。容量が大きいほど、木は短くなりますが、特定の空間領域を特定するのに必要な時間は容量に対して線形に増加します。

# 参考文献

[guttman84] “R-Trees: A Dynamic Index Structure for Spatial Searching” A. Guttman, Proc. 1984 ACM-SIGMOD Conference on Management of Data (1985), 47-57. [beckmann90] "The R*-tree: an efficient and robust access method for points and rectangles" N. Beckmann, H.P. Kriegel, R. Schneider, B. Seeger, Proc. 1990 ACM SIGMOD international conference on Management of data (1990), p.322
