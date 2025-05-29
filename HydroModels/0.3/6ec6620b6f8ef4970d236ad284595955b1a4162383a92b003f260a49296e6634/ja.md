```
NeuralFlux{N} <: AbstractNeuralFlux
```

水文学モデルにおけるニューラルネットワークベースのフラックスコンポーネントを表します。型パラメータ `N` は、型レベルでコンポーネント名をエンコードするために使用され、より良い型の安定性を提供します。

# 引数

  * `inputs::Vector{Num}`: 入力変数のベクター
  * `outputs::Vector{Num}`: 出力変数のベクター
  * `chain::LuxCore.AbstractLuxLayer`: ニューラルネットワークモデル
  * `name::Union{Symbol,Nothing}=nothing`: オプションのフラックス識別子
  * `chain_name::Union{Symbol,Nothing}=nothing`: オプションのニューラルネットワーク識別子

# フィールド

  * `chain::LuxCore.AbstractLuxLayer`: ニューラルネットワークモデル
  * `func::Function`: フラックス計算のために生成された関数
  * `infos::NamedTuple`: コンポーネントメタデータ

# モデル構造

ニューラルフラックスモデルは以下で構成されています：

  * 入力変数: ニューラルネットワークに供給される外部変数
  * 出力変数: ニューラルネットワークの予測
  * ニューラルネットワーク: 機械学習モデル
  * 生成された関数: 計算のための最適化された実装

## メタデータコンポーネント

`infos` フィールドは以下を追跡します：

  * `inputs`: 入力変数名
  * `outputs`: 出力変数名
  * `nns`: ニューラルネットワーク名
  * `nn_inputs`: ニューラルネットワーク入力名
  * `nn_outputs`: ニューラルネットワーク出力名
