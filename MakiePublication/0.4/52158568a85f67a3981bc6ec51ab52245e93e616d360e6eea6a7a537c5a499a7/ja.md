```
theme_jcap(; kwargs...)
```

JCAP（宇宙論および粒子物理学のジャーナル）用の図を生成するためのMakieテーマを作成します。

使用法は[`theme_acs`](@ref)と同じですが、図の`width=6.08948`です。`width`の値は`\uselengthunit{in}\printlength{\linewidth}`から取得され、440ptに対応します。

JCAPは単一列のため、`theme_jcap_1col`および`theme_jcap_2col`は定義されていません。

他に[`theme_acs`](@ref)、[`theme_aps`](@ref)、[`theme_jhep`](@ref)、[`theme_rsc`](@ref)、および[`theme_web`](@ref)も参照してください。
