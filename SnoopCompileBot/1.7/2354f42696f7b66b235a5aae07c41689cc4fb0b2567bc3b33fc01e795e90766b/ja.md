```
snoop_bot(config::BotConfig, path_to_example_script::String, test_modul=Main; snoop_mode=:auto)
```

プリコンパイルステートメントをプリコンパイルスクリプトを使用して生成します。`config`は[`BotConfig`](@ref)によって生成できます。`path_to_example_script`は絶対パスであることが望ましいです。例のスクリプトは`test_modul`で指定されたモジュール内で実行されます。`snoop_mode`は`:auto`、`:snoopi`（[`SnoopCompileCore.@snoopi`](@ref)を実行するため）、または`:snoopc`（[`SnoopCompileCore.@snoopc`](@ref)を実行するため）であり、`:auto`はサポートされているJuliaのバージョンで`:snoopi`を選択します。

より完全な概要については、[オンラインドキュメント](https://timholy.github.io/SnoopCompile.jl/stable/bot/)を参照してください。

# 拡張ヘルプ

## 例

この場合、ボット実行スクリプトはプリコンパイルスクリプトと同じディレクトリに配置されているため、`@__DIR__`を使用してそれを見つけることができます：

```julia
using SnoopCompile

snoop_bot(BotConfig("MatLang"), "$(@__DIR__)/example_script.jl")
```
