```
HANNA <: ActivityModel
HANNA(components;
puremodel = nothing,
userlocations = String[],
pure_userlocations = String[],
verbose = false,
reference_state = nothing)
```

## 入力パラメータ

  * `canonicalsmiles`: コンポーネントの標準SMILES（RDKitを使用）表現
  * `Mw`: 単一パラメータ（`Float64`）（オプション） - 分子量 `[g/mol]`

## 入力モデル

  * `puremodel`: 純圧依存特性を計算するためのモデル

## 説明

一貫した活動係数予測のためのハード制約ニューラルネットワーク（HANNA v1.0.0）。この実装は、[この](https://github.com/tspecht93/HANNA) GitHubリポジトリに基づいています。HANNAは、ドルトムントデータバンクからのすべての利用可能な二元VLEデータ（最大10バール）および制限活動係数でトレーニングされました。HANNAはこれまでのところ二元混合物のみでテストされています。多成分混合物への拡張は実験的です。

モデルを使用するには、パッケージ`ClapeyronHANNA`をインストールしてロードする必要があります（以下の例を参照）。

## 例

```julia
using Clapeyron, ClapeyronHANNA

components = ["water","isobutanol"]
Mw = [18.01528, 74.1216]
smiles = ["O", "CC(C)CO"]

model = HANNA(components,userlocations=(;Mw=Mw, canonicalsmiles=smiles))
# model = HANNA(components) # コンポーネントがデータベースにある場合も動作します 
```

## 参考文献

1. Specht, T., Nagda, M., Fellenz, S., Mandt, S., Hasse, H., Jirasek, F., HANNA: 一貫した活動係数予測のためのハード制約ニューラルネットワーク。Chemical Science 2024. [10.1039/D4SC05115G](https://doi.org/10.1039/D4SC05115G).
