```
IsLinearParameter(DM::DataModel, MLE::AbstractVector) -> BitVector
```

モデル関数 `model(x,θ)` がどのパラメータに関して線形であるかをチェックし、線形性を示す `true` を含むブール値のベクトルを返します。このテストは、2つのランダムな構成 $\theta_1, \theta_2 \in \mathcal{M}$ のヤコビアンを列ごとに比較することによって行われます。
