```
HydroFlux{N} <: AbstractHydroFlux
```

水文学モデルにおける数学的公式を持つシンプルなフラックスコンポーネントを表します。

# 引数

  * `inputs::Vector{Num}`: 入力変数のベクトル
  * `outputs::Vector{Num}`: 出力変数のベクトル
  * `params::Vector{Num}=Num[]`: パラメータ変数のベクトル
  * `exprs::Vector{Num}`: 出力計算のための式のベクトル
  * `name::Union{Symbol,Nothing}=nothing`: オプションのフラックス識別子

# フィールド

  * `exprs::Vector{Num}`: 数学的式のベクトル
  * `func::Function`: フラックス計算のために生成された関数
  * `infos::NamedTuple`: メタデータ (inputs::Vector{Num}, outputs::Vector{Num}, params::Vector{Num})

## モデル構造

フラックスモデルは以下で構成されています：

  * 入力変数: 計算に使用される外部変数
  * 出力変数: 計算されたフラックス結果
  * パラメータ: 計算に使用されるモデルパラメータ
  * 式: 関係を定義する数学的公式

## メタデータコンポーネント

`infos`フィールドは以下を追跡します：

  * `inputs`: 入力変数名
  * `outputs`: 出力変数名
  * `params`: パラメータ名
