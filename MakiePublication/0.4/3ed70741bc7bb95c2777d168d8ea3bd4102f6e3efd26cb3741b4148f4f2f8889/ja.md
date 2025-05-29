```
theme_jhep(; kwargs...)
```

JHEP（高エネルギー物理学ジャーナル）用の図を生成するためのMakieテーマを作成します。

使用法は[`theme_acs`](@ref)と同じですが、図の`width=5.95393`です。`width`の値は`\uselengthunit{in}\printlength{\linewidth}`から取得されます。

JHEPは単一カラムなので、`theme_jhep_1col`および`theme_jhep_2col`は定義されていません。

他に[`theme_acs`](@ref)、[`theme_aps`](@ref)、[`theme_jcap`](@ref)、[`theme_rsc`](@ref)、および[`theme_web`](@ref)も参照してください。
