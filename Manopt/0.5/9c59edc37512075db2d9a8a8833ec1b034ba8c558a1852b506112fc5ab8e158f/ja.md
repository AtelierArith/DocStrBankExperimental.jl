```
ManifoldAlternatingGradientObjective{E<:AbstractEvaluationType,TCost,TGradient} <: AbstractManifoldGradientObjective{E}
```

交互勾配目的関数は以下で構成されます。

  * コスト関数 $F(x)$
  * 勾配 $\operatorname{grad}F$ は次のいずれかです。

      * 接ベクトル `X` を `M` 上で返す1つの関数 $\operatorname{grad}F$ として与えられるか
      * 勾配の各成分を返す勾配関数の配列 $\operatorname{grad}F_i$, `ì=1,…,n` として

    これらは割り当てまたは変異のバリアントである可能性がありますが、両方の混合はありません。

!!! note
    この目的関数は通常、`Manifolds.jl` の `ProductManifold` を使用して定義されるため、`Manifolds.jl` をロードする必要があります。


# コンストラクタ

```
ManifoldAlternatingGradientObjective(F, gradF::Function;
    evaluation=AllocatingEvaluation()
)
ManifoldAlternatingGradientObjective(F, gradF::AbstractVector{<:Function};
    evaluation=AllocatingEvaluation()
)
```

コストをオプションとして持ち、勾配を1つの関数（配列を返す）または関数のベクトルとして持つ交互勾配問題を作成します。
