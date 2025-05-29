```
LeftSemidirectProductGroupOperation{O1,O2,A} <: SemiDirectProductGroupOperation{O1,O2,A}
```

半直 Lie 群積をモデル化するための構造体。

$$
(\mathcal N, ⋄)
$$

と $(\mathcal H, ⋆)$ をそれぞれ群演算 $⋄$ と $⋆$ を持つ二つの Lie 群とし、群作用 $σ: \mathcal H×\mathcal N → \mathcal N$ を考えます。cf [`AbstractLeftGroupActionType`](@ref)。

ここでは、$\mathcal N$ 上の写像の族として $σ_h: \mathcal N → \mathcal N$ の表記を使用します。

次に、積多様体 $\mathcal N×\mathcal H$ 上の群演算 $∘$ を次のように定義します。

$$
    (h_1,n_1) ∘ (h_2,n_2) := (h_1 ⋆ h_2, σ_{h_2}(n_1) ⋄ n_2).
$$

詳細については [HilgertNeeb:2012; Definition 9.2.22](@cite) の第二の定義を参照してください。

# コンストラクタ

```
LeftSemidirectProductGroupOperation(
    op1::AbstractGroupOperation,
    op2::AbstractGroupOperation,
    action::AbstractGroupActionType
)
```

# パラメータ

  * `op1::AbstractGroupOperation`: $\mathcal H$ 上の群演算 $⋄$
  * `op2::AbstractGroupOperation`: $\mathcal N$ 上の群演算 $⋆$
  * `action::AbstractGroupActionType` $\mathcal H$ が $\mathcal N$ に対して持つ群作用 $σ$
