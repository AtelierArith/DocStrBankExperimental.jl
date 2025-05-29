```julia
compilefis(
    fname::AbstractString,
    fis::FuzzyLogic.AbstractFuzzySystem
) -> Any
compilefis(
    fname::AbstractString,
    fis::FuzzyLogic.AbstractFuzzySystem,
    name::Symbol
) -> Any

```

ファジィ推論システムをスタンドアロンのJuliaコードにコンパイルします。最初の引数が文字列の場合、指定されたファイルにコードを書き込みます。それ以外の場合は、コードのJulia式を返します。

### 入力

  * `fname::AbstractString` – 書き込むファイル
  * `fis::AbstractFuzzySystem` – コンパイルするファジィシステム
  * `name::Symbol` – 生成される関数の名前、デフォルトは `fis.name`

### 注意事項

タイプ1の推論システムのみがサポートされています。
