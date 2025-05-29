```julia
readfis(file::String) -> FuzzyLogic.AbstractFuzzySystem
readfis(
    file::String,
    fmt::Union{Nothing, Symbol}
) -> FuzzyLogic.AbstractFuzzySystem

```

指定されたフォーマットを使用してファイルからファジィシステムを読み込みます。

### 入力

  * `file::String` – 読み込むファイルへのパス。
  * `fmt::Union{Symbol,Nothing}` – ファイルの入力フォーマット。`nothing`の場合、ファイル拡張子から推測されます。

サポートされているフォーマットは次のとおりです。

  * `:fcl` – ファジィ制御言語（対応するファイル拡張子 `.fcl`）
  * `:fml` – ファジィマークアップ言語（対応するファイル拡張子 `.xml`）
  * `:matlab` – Matlab fis（対応するファイル拡張子 `.fis`）
