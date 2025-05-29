```
theme_joss(; kwargs...)
```

JOSS（The Journal of Open Source Software）用の図を生成するためのMakieテーマを生成します。

使用法は[`theme_acs`](@ref)と同じですが、図の`width=5.36066`です。`width`の値は`\uselengthunit{in}\printlength{\linewidth}`から取得されます。

JOSSは単一列なので、`theme_joss_1col`および`theme_joss_2col`は定義されていません。

他に[`theme_acs`](@ref)、[`theme_aps`](@ref)、[`theme_jcap`](@ref)、[`theme_rsc`](@ref)、および[`theme_web`](@ref)も参照してください。
