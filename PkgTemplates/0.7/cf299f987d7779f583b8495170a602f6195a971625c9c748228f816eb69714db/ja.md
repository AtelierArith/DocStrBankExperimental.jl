```
Formatter(;
    file="~/.julia/packages/PkgTemplates/MepaC/templates/.JuliaFormatter.toml",
    style="nostyle"
)
```

`.JuliaFormatter.toml` ファイルを作成します。このファイルは、[JuliaFormatter.jl](https://github.com/domluna/JuliaFormatter.jl) と Julia VSCode 拡張機能によって自動コードフォーマットを設定するために使用されます。

このファイルはユーザーによって完全にカスタマイズ可能です。詳細は [JuliaFormatter.jl docs](https://domluna.github.io/JuliaFormatter.jl/stable/) を参照してください。

## キーワード引数

  * `file::String`: `.JuliaFormatter.toml` のテンプレートファイル。
  * `style::String`: スタイル名。デフォルトは空のスタイルのための `"nostyle"` ですが、完全に事前設定されたスタイルの `("sciml", "blue", "yas")` のいずれかにすることもできます。
