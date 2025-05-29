```
effects(design::AbstractDict, model::MixedModel, boot::MixedModelBootstrap;
        eff_col=nothing, err_col=:err, typical=mean,
        lower_col=:lower, upper_col=:upper, invlink=identity,
        level=nothing)
```

ブートストラップの結果を使用して、経験的な誤差推定を計算します（分散共分散行列を使用する代わりに）。

!!! warning
    このメソッドは実験的であり、将来のリリースでデフォルトが変更されるか、完全に消える可能性があります！

