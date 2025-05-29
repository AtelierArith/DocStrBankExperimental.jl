```
effects(design::AbstractDict, model::RegressionModel;
        eff_col=nothing, err_col=:err, typical=mean,
        lower_col=:lower, upper_col=:upper, invlink=identity,
        vcov=StatsBase.vcov, level=nothing)
```

`design`によって指定された`effects`を計算します。

これは[`effects!`](@ref)の便利なラッパーです。参照グリッドを指定する代わりに、各予測子のレベル/値を含む辞書が指定されます。これにより、完全に交差したデザインを表す参照グリッドに展開されます。さらに、信頼区間の下限と上限を表す2つの追加列が作成されます。デフォルトの`level=nothing`は[resp-err, resp+err]に対応し、`level=0.95`は95%信頼区間に対応します。

さらに[`AutoInvLink`](@ref)も参照してください。
