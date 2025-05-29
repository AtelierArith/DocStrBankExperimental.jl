`SemImplied`のサブタイプで、シンボリック前計算を用いたRAM表記を実装します。

# コンストラクタ

```
RAMSymbolic(;
    specification,
    vech = false,
    gradient = true,
    hessian = false,
    approximate_hessian = false,
    meanstructure = false,
    kwargs...)
```

# 引数

  * `specification`: `RAMMatrices`または`ParameterTable`オブジェクト
  * `meanstructure::Bool`: モデルに平均構造はありますか？
  * `gradient::Bool`: 勾配ベースの最適化が使用されていますか？
  * `hessian::Bool`: ヘッセ行列ベースの最適化が使用されていますか？
  * `approximate_hessian::Bool`: ヘッセ行列ベースの最適化の場合：ヘッセ行列を近似すべきですか？
  * `vech::Bool`: Σの半ベクトル化を計算すべきですか（完全な行列の代わりに）？  （損失関数のいずれかがSemWLSである場合、自動的にtrueに設定されます）

# 拡張ヘルプ

## インターフェース

  * `param_labels(::RAMSymbolic)`-> パラメータIDのベクトル
  * `nparams(::RAMSymbolic)` -> パラメータの数
  * `ram.Σ` -> モデルが示唆する共分散行列
  * `ram.μ` -> モデルが示唆する平均ベクトル

ヤコビアン（`gradient!`呼び出しでのみ利用可能）

  * `ram.∇Σ` -> $∂vec(Σ)/∂θᵀ$
  * `ram.∇μ` -> $∂μ/∂θᵀ$
  * `ram.∇Σ_function` -> `∇Σ`をその場で上書きする関数、すなわち`∇Σ_function(∇Σ, θ)`。通常、これを使用することは望ましくなく、単に`ram.∇Σ`をクエリすることをお勧めします。

ヘッセ行列 ヘッセ行列の計算はより複雑です。したがって、オンラインドキュメントで説明し、関連するインターフェースはここでは省略します。

## RAM表記

モデルが示唆する共分散行列は次のように計算されます。

$$
    \Sigma = F(I-A)^{-1}S(I-A)^{-T}F^T
$$

平均構造を持つモデルの場合、モデルが示唆する平均は次のように計算されます。

$$
    \mu = F(I-A)^{-1}M
$$
