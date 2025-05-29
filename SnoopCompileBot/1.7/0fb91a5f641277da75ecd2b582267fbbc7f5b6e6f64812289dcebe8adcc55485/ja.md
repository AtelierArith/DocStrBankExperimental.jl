```
snoop_bench(config::BotConfig, path_to_example_script::String, test_modul::Module=Main; snoop_mode=:auto)
```

プリコンパイルステートメントの影響をベンチマークするために、プリコンパイルありとなしでスクリプトを実行します。`config`は[`BotConfig`](@ref)によって生成できます。`path_to_example_script`は絶対パスであることが望ましいです。例のスクリプトは、`test_modul`で指定されたモジュール内で実行されます。`snoop_mode`は、`:auto`、`:snoopi`（[`SnoopCompileCore.@snoopi`](@ref)を使用してテストするため）、または`:runtime`（`@timev`を使用してスクリプトの総実行時間を測定するため）に設定できます。`:auto`は、サポートされているJuliaのバージョンで`:snoopi`を選択します。

より完全な概要については、[オンラインドキュメント](https://timholy.github.io/SnoopCompile.jl/stable/bot/)を参照してください。

# 拡張ヘルプ

## 例

この場合、ベンチマークスクリプトはプリコンパイルスクリプトと同じディレクトリに配置されているため、`@__DIR__`を使用して見つけることができます：

```julia
using SnoopCompile

snoop_bench(BotConfig("MatLang"), "$(@__DIR__)/example_script.jl")
```

`@__DIR__`の代わりに（たとえば、ベンチマークスクリプトをパッケージの外に保存している場合）、[`pathof_noload`](@ref)を使用してパッケージを見つけることができます。 ```
