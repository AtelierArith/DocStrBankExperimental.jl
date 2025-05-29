```julia
getManifoldPartial(M, partial; ...)
getManifoldPartial(M, partial, repr; ...)
getManifoldPartial(M, partial, repr, offset; doError)

```

いわゆるフル次元多様体は、いくつかの次元にわたって小さな部分多様体に還元される可能性があり、新しくプログラム的に生成された`<:AbstractManifold`を返します。この関数は、必要な部分次元の点表現を還元することもオプションで可能です。

例

```julia
using Manifolds
using ApproxManifoldProducts

# 2Dの平行移動と回転のなじみのある多様体
M = SpecialEuclidean(2)

# 平行移動成分のみの新しい部分を作成
M_x, _ = getManifoldPartial(M,[1;])
# x次元に対応する新しいTranslationGroup(1)を返します

# 表現は平行移動と回転行列の半直積です
u0 = ArrayPartition([0.0;0],[1 0; 0 1.0])

# 既知の座標は[x,y,θ]です。例えば
#   vee(M,identity_element(M,u0),log(M,identity_element(M,u0),u0))
#   この例では[0;0;0]です

# 回転成分のみの別の新しい部分を作成
M_rot, u_rot = getManifoldPartial(M,[3],u0)
# SpecialOrthogonal(2)の情報を返します

# yとθのみの別の新しい部分を作成
M_yθ, u_yθ = getManifoldPartial(M,[2;3],u0)
# ProductArray(TranslationGroup(1),SpecialOrthogonal(2))として新しい多様体情報を返します
```

ノート

  * 興味のある部分次元は、座標次元の`AbstractVector{Int}`を介して定義されます。
  * より一般的な解に向けた遷移ステップとして座標に従うと仮定されています
  * 複数の多様体を結合する唯一の方法はProductManifoldであると仮定しています
  * まだ実験的です。

開発ノート

  * FIXME 半直積または作用情報が失われており、現在は単純なProduct多様体の仮定がなされています。

関連

[`getManifold`](@ref), [`AbstractManifold`], [`ProductManifold`], [`GroupManifold`], [`ArrayPartition`]
