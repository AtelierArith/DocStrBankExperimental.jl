```
LieGroup{𝔽, O<:AbstractGroupOperation, M<:AbstractManifold{𝔽}} <:  AbstractLieGroup{𝔽, O, M}
```

リー群 $\mathcal G$ を表します。

*リー群* $\mathcal G$ は、群演算 $∘: \mathcal G×\mathcal G → \mathcal G$（[`compose`](@ref) を参照）および逆演算 $⋅^{-1}: \mathcal G → \mathcal G$（[`inv`](@ref) を参照）が滑らかであるように、マンifold の構造を持つ群です。例えば、[HilgertNeeb:2012; Definition 9.1.1](@cite) を参照してください。

リー群は、ノルウェーの数学者 [Marius Sophus Lie](https://en.wikipedia.org/wiki/Sophus_Lie) (1842–1899) にちなんで名付けられました。

# フィールド

  * `manifold`: [`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`) $\mathcal M$
  * `op`: そのマンifold 上の [`AbstractGroupOperation`](@ref) $∘$

# コンストラクタ

```
LieGroup(M::AbstractManifold, op::AbstractGroupOperation)
```

マンifold `M` と群演算 `op` に基づいてリー群を生成します。ベクトルはデフォルトでリー代数に格納されます。
