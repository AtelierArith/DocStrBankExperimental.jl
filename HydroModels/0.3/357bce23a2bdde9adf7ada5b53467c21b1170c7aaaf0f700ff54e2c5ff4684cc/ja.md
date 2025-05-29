```
(flux::AbstractHydroFlux)(input::AbstractArray, params::ComponentVector; kwargs...)
```

水のフラックスを計算するために、入力データにHydroFluxモデルを適用します。

# 引数

  * `input::AbstractArray`: 次のような次元を持つ入力データ配列：

      * `Matrix`: 形状が (variables, timesteps) の時系列データ
      * `Array{3}`: 形状が (variables, nodes, timesteps) の分散データ
  * `params::ComponentVector`: コンポーネントベクトルに整理されたモデルパラメータ
  * `kwargs`: 追加のキーワード引数：

      * `ptyidx::AbstractVector{Int}`: 分散実行のためのパラメータタイプインデックス（デフォルト：すべてのノード）

# 戻り値

  * `Matrix`: 2D入力の場合、形状が (output_variables, timesteps) の行列を返します
  * `Array{3}`: 3D入力の場合、形状が (output_variables, nodes, timesteps) の配列を返します

# 説明

この関数は、入力時系列データにフラックス計算を適用し、単一ノードおよび分散（マルチノード）シミュレーションの両方をサポートします。分散実行の場合、パラメータは自動的にノードの数に合わせて拡張されます。

## 入力データ構造

  * 変数は最初の次元に沿って配置する必要があります
  * 分散実行の場合、ノードは2番目の次元に沿っています
  * 時間ステップは常に最後の次元にあります

## パラメータ処理

  * 単一ノード：パラメータはそのまま使用されます
  * マルチノード：パラメータはノード数に合わせて `ptyidx` を使用して拡張されます
  * コンポーネントパラメータは型の安定性を維持します

## 例

```julia
# 単一ノードシミュレーション
flux = HydroFlux([P, E] => [Q], params=[k], exprs=[k*P - E])
output = flux(input, params)  # input: (2, timesteps)

# マルチノードシミュレーション
output = flux(input, params, ptyidx=1:n_nodes)  # input: (2, n_nodes, timesteps)
```
