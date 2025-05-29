```
function prep(f::StatsModels.TermOrTerms, inputData::DataFrame;userHints=Dict{Symbol,Any}(),path2ped=[],priorVCV=[])
```

  * `NextGP`はモデル式（`f`）と固定効果デザイン行列の生成のために`StatsModels.jl`パッケージに依存しています。
  * モデル式（`f`）および固定効果コーディング仕様（例：効果コーディングまたはダミーコーディング）の詳細は[`StatsModels.jl`](https://juliastats.org/StatsModels.jl/latest/)で確認できます。
  * ランダム効果のデザイン行列は、モデル内でユーザーがモデル項をどのように定義したかに応じて、内部関数または`StatsModels.jl`の`modelcols`を使用して生成されます。
  * マーカーデータを読み込み、列を平均中心化します。
  * 最後にlhsベクトルとrhs行列を返します。
  * デフォルトでは：

      * すべての`Int`型のrhs変数は`Categorical`にされ、
      * すべての`String`型のrhs変数（`Categorical`にされたものも含む）はダミーコーディングされますが、`userHints`でユーザーが定義したものは除外されます。
      * すべての`Float`型のrhs変数は中心化されます。
