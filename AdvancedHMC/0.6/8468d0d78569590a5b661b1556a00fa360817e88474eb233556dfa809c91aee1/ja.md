```
sample(
    rng::AbstractRNG,
    h::Hamiltonian,
    κ::AbstractMCMCKernel,
    θ::AbstractVecOrMat{T},
    n_samples::Int,
    adaptor::AbstractAdaptor=NoAdaptation(),
    n_adapts::Int=min(div(n_samples, 10), 1_000);
    drop_warmup::Bool=false,
    verbose::Bool=true,
    progress::Bool=false
)
```

提案 `κ` の下でハミルトニアン `h` を使用して `n_samples` サンプルをサンプリングします。

  * ランダム性は `rng` によって制御されます。 

      * `rng` が提供されていない場合、`GLOBAL_RNG` が使用されます。
  * 初期点は `θ` によって与えられます。
  * アダプタは `adaptor` によって設定され、デフォルトは適応なしです。

      * それは `n_adapts` ステップの適応を行い、デフォルトは `1_000` と `n_samples` の 10% の最小値です。
  * `drop_warmup` は適応フェーズ中にサンプルをドロップするかどうかを制御します。
  * `verbose` は冗長性を制御します。
  * `progress` は進捗メーターを表示するかどうかを制御します。
