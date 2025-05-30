```julia
estimation(
    estset::MomentMatching.EstimationSetup;
    npmm,
    cs,
    aux,
    presh,
    xlocstart,
    saving,
    saving_bestmodel,
    number_bestmodel,
    filename_suffix,
    errorcatching,
    vararg...
)

```

[`EstimationSetup`](@ref) のインスタンスが与えられたときにモデルパラメータを推定します。

デフォルトでない推定ケースを実行する必要がある場合はカスタマイズできます。ローカルステージのみが実行される場合は初期推定値を受け入れます。
