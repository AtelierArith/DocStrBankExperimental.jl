```
replay(instructions::Vector{<:AbstractString}, buf::IO; kwargs...)
```

与えられた指示からREPL出力を再生します。

## キーワード引数

### 再生オプション

  * `use_ghostwriter`: ゴーストライターモードを有効にするフラグ。(デフォルト: `true`)

### Juliaオプション

  * `julia_project`: juliaプロセスが実行されるプロジェクトへのパス。(デフォルト: `@.`)
  * `cmd`: juliaプロセスの追加コマンド。(デフォルト: `"--color=yes"`)
