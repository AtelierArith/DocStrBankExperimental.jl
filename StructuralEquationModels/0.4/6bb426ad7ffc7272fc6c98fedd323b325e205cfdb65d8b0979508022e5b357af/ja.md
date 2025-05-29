モデルが暗示する共分散と平均をRAM表記法で表現します。

# コンストラクタ

```
RAM(;specification,
    meanstructure = false,
    gradient = true,
    kwargs...)
```

# 引数

  * `specification`: `RAMMatrices`または`ParameterTable`オブジェクトのいずれか
  * `meanstructure::Bool`: モデルに平均構造はありますか？
  * `gradient::Bool`: 勾配ベースの最適化が使用されていますか？

# 拡張ヘルプ

## RAM表記法

モデルが暗示する共分散行列は次のように計算されます。

$$
    \Sigma = F(I-A)^{-1}S(I-A)^{-T}F^T
$$

平均構造を持つモデルの場合、モデルが暗示する平均は次のように計算されます。

$$
    \mu = F(I-A)^{-1}M
$$

## インターフェース

  * `param_labels(::RAM)`-> パラメータラベルのベクトル
  * `nparams(::RAM)` -> パラメータの数
  * `ram.Σ` -> モデルが暗示する共分散行列
  * `ram.μ` -> モデルが暗示する平均ベクトル

現在のパラメータ値に対するRAM行列：

  * `ram.A`
  * `ram.S`
  * `ram.F`
  * `ram.M`

パラメータベクトル`θ`に関するRAM行列のヤコビ行列：

  * `ram.∇A` -> $∂vec(A)/∂θᵀ$
  * `ram.∇S` -> $∂vec(S)/∂θᵀ$
  * `ram.∇M` = $∂M/∂θᵀ$

それぞれのRAM行列における各パラメータのインデックスのベクトル：

  * `ram.A_indices`
  * `ram.S_indices`
  * `ram.M_indices`

追加のインターフェース

  * `ram.F⨉I_A⁻¹` -> $F(I-A)^{-1}$
  * `ram.F⨉I_A⁻¹S` -> $F(I-A)^{-1}S$
  * `ram.I_A` -> $I-A$

勾配！呼び出しでのみ利用可能：

  * `ram.I_A⁻¹` -> $(I-A)^{-1}$
