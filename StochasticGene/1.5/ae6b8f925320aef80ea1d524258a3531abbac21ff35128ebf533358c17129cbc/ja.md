```
readrates(infolder::String, label::String, gene::String, G::Int, R::Int, S::Int, insertstep::Int, nalleles::Int, ratetype::String="median")
```

ファイルからレートを読み込みます。

# 引数

  * `infolder::String`: レートファイルを保持するフォルダー。
  * `label::String`: レートファイルのラベル。
  * `gene::String`: 遺伝子名。
  * `G::Int`: G状態の数。
  * `R::Int`: Rステップの数。
  * `S::Int`: スプライス状態の数。
  * `insertstep::Int`: スプライシングが始まるRステップ。
  * `nalleles::Int`: アレルの数。
  * `ratetype::String`: 読み込むレートのタイプ。デフォルトは`"median"`。

# 戻り値

  * `Array{Float64, 2}`: ファイルから読み込まれたレート。

# 例

```julia
rates = readrates("data", "label", "gene", 3, 5, 2, 1, 2, "mean")
```
