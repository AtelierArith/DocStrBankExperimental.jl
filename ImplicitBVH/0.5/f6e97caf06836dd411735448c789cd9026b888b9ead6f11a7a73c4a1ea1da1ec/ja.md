```julia
struct BVH{I<:Integer, VN<:(AbstractVector), VL<:(AbstractVector), VM<:(AbstractVector), VO<:(AbstractVector)}
```

幾何プリミティブ（例えばメッシュ内の三角形）のバウンディングボリュームから構成される [`ImplicitTree`](@ref) の葉を形成するイテラブルから構築された暗黙のバウンディングボリューム階層。葉とその上のマージされたノードは異なるタイプを持つことができます - 例えば、マージされた葉には `BSphere{Float64}`、より大きな `BBox{Float64}` があります。

初期の幾何プリミティブは、モートンエンコードされた座標に従ってソートされます。モートンエンコーディングに使用される符号なし整数型は `Union{UInt16, UInt32, UInt64}` の中から選択できます。

最後に、ツリーは指定された `built_level` まで不完全に構築され、後でこのレベルから下に向かって接触検出を開始できます。例えば：

```
5つのバウンディングボリュームからの暗黙のツリー - すなわち、実際の葉

ツリーレベル          ノードと葉               構築    下にトラバース
    1                     1                         Ʌ              |
    2             2               3                 |              |
    3         4       5       6        7v           |              |
    4       8   9   10 11   12 13v  14v  15v        |              V
            -------実際の------- ---仮想の---
```

注意：葉を変更しないようにするため（別の場所に保存することができ、コピーを作成するのを避けるため）、BVHの葉のソート順を `order` フィールド内に保存します。

# メソッド

```
# BVHを構築する通常のコンストラクタ
BVH(
    bounding_volumes::AbstractVector{L},
    node_type::Type{N}=L,
    morton_type::Type{U}=UInt32,
    built_level=1,
    cache::Union{Nothing, BVH}=nothing;
    options=BVHOptions(),
) where {L, N, U <: MortonUnsigned}
```

# フィールド

  * `tree::`[`ImplicitTree`](@ref)`{I <: Integer}`
  * `nodes::VN <: AbstractVector`
  * `leaves::VL <: AbstractVector`
  * `mortons::VM <: AbstractVector`
  * `order::VO <: AbstractVector`
  * `built_level::Int`

# 例

バウンディングスフィアとデフォルトの64ビット型を使用した簡単な使用法：

```jldoctest
using ImplicitBVH
using ImplicitBVH: BSphere

# 簡単なバウンディングスフィアを生成
bounding_spheres = [
    BSphere([0., 0., 0.], 0.5),
    BSphere([0., 0., 1.], 0.6),
    BSphere([0., 0., 2.], 0.5),
    BSphere([0., 0., 3.], 0.4),
    BSphere([0., 0., 4.], 0.6),
]

# BVHを構築
bvh = BVH(bounding_spheres)

# 接触検出のためにBVHをトラバース
traversal = traverse(bvh)
@show traversal.contacts;
;

# 出力
traversal.contacts = Tuple{Int32, Int32}[(1, 2), (2, 3), (4, 5)]
```

葉に `Float32` バウンディングスフィア、上のノードに `Float32` バウンディングボックス、`UInt32` モートンコードを使用：

```jldoctest
using ImplicitBVH
using ImplicitBVH: BBox, BSphere

# 簡単なバウンディングスフィアを生成
bounding_spheres = [
    BSphere{Float32}([0., 0., 0.], 0.5),
    BSphere{Float32}([0., 0., 1.], 0.6),
    BSphere{Float32}([0., 0., 2.], 0.5),
    BSphere{Float32}([0., 0., 3.], 0.4),
    BSphere{Float32}([0., 0., 4.], 0.6),
]

# BVHを構築
bvh = BVH(bounding_spheres, BBox{Float32}, UInt32)

# 接触検出のためにBVHをトラバース
traversal = traverse(bvh)
@show traversal.contacts;
;

# 出力
traversal.contacts = Tuple{Int32, Int32}[(1, 2), (2, 3), (4, 5)]
```

レベル2までBVHを構築し、レベル3から下にトラバースを開始し、前のトラバースキャッシュを再利用：

```julia
bvh = BVH(bounding_spheres, BBox{Float32}, UInt32, 2)
traversal = traverse(bvh, 3, traversal)
```

新しいBVHのために以前のBVHメモリを再利用（具体的には、ノード、モートン、オーダーベクターを再利用しますが、葉は再利用しません）：

```julia
bvh = BVH(bounding_spheres, BBox{Float32}, UInt32, 1, bvh)
```
