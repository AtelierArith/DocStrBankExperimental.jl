```julia
indexvector(
    mode::MomentMatching.EstimationMode,
    modelname::String
)

```

実際に推定されるパラメータを可能なフルリストから選択する論理ベクトルを作成します（[`parambounds`](@ref)のfull*labelsを参照）。結果のベクトルの`i`番目の要素が`true`であれば、`full*labels`の`i`番目のパラメータが推定されることになります。

推定モードに対してマッチングメソッドが別途定義されていない場合、すべての可能なパラメータが常に推定されると仮定され、したがって`true`の値のベクトルがデフォルトとなります。
