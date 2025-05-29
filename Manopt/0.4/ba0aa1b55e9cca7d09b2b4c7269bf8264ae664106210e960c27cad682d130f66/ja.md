```
ConstrainedProblem{
    TM <: AbstractManifold,
    O <: AbstractManifoldObjective
    HR<:Union{AbstractPowerRepresentation,Nothing},
    GR<:Union{AbstractPowerRepresentation,Nothing},
    HHR<:Union{AbstractPowerRepresentation,Nothing},
    GHR<:Union{AbstractPowerRepresentation,Nothing},
} <: AbstractManoptProblem{TM}
```

制約付き問題は、等式および不等式制約の（ベクトルの）勾配の異なる範囲を特徴とする場合があります。

範囲は、メモリを割り当て、要素に正しくアクセスするためにいくつかの場所で必要です。動作は次のようになります。

目的が次のようであると仮定します。

$$
\begin{aligned}
 \operatorname*{arg\,min}_{p ∈\mathcal{M}} & f(p)\\
 \text{subject to } &g_i(p)\leq0 \quad \text{ for all } i=1,…,m,\\
 \quad &h_j(p)=0 \quad \text{ for all } j=1,…,n.
\end{aligned}
$$

この場合、勾配は（古典的に）成分勾配のベクトルとして考えることができます。たとえば、$\bigl(\operatorname{grad} g_1(p), \operatorname{grad} g_2(p), …, \operatorname{grad} g_m(p) \bigr)$のように。

別の解釈では、これは$P = (p,…,p) \in \mathcal M^m$における接空間の点と考えることができます。したがって、[`PowerManifold`](@extref `ManifoldsBase.PowerManifold`) :\mathcal M^mへの接空間です。この場合、これが[`NestedPowerRepresentation`](@extref)である場合、以前の解釈と一致しますが、パワーマニフォールド上では、より効率的な表現が存在します。

要素にアクセスするには、範囲を指定する必要があります。これがこの問題の目的です。

# コンストラクタ

```
ConstrainedManoptProblem(
    M::AbstractManifold,
    co::ConstrainedManifoldObjective;
    range=NestedPowerRepresentation(),
    gradient_equality_range=range,
    gradient_inequality_range=range
    hessian_equality_range=range,
    hessian_inequality_range=range
)
```

`gradient_equality_range`と`gradient_inequality_range`の両方に対して[`AbstractPowerRepresentation`](@extref ManifoldsBase.AbstractPowerRepresentation)を指定して、制約付きManopt問題を作成します。
