covrowmask、geneticrowmaskは、共変量ファイルと遺伝子ファイルの一致するインデックスを返します。平均、ランダム効果、および被験者内分散の数式、グループ化（id）変数、データフレーム（またはテーブル）、および遺伝子ファイルの順序でのIDのベクターを入力します。

```julia
covrowinds, geneticrowinds = matchindices(@formula(y ~ 1 + x), 
    @formula(y ~ 1), 
    @formula(y ~ 1 + z), 
    idvar, df, geneticsamples)

```
