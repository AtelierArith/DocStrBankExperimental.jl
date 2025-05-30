```julia
indexvector(
    mode::MomentMatching.EstimationMode,
    modelname::String
)

```

可能なフルリストから実際に推定されるパラメータを選択する論理ベクトルを作成します（[`parambounds`](@ref)のfull*labelsを参照）。結果のベクトルの`i`番目の要素が`true`であれば、`full*labels`の`i`番目のパラメータが推定されることになります。

EstimationModeに対してマッチングメソッドが別途定義されていない場合、すべての可能なパラメータが常に推定されると仮定され、そのため`true`の値のベクトルがデフォルトとなります。
