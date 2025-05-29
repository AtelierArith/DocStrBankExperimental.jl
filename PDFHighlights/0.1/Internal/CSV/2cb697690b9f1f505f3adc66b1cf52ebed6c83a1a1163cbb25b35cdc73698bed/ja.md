```
import_highlights(csv::String, target::String; quiet::Bool=false) -> Nothing
```

PDFファイルまたはPDFファイルのディレクトリからCSVファイルにハイライト（および関連データ）をインポートします。

# 引数

  * `csv::String`: CSVファイルへの絶対パスまたは相対パス
  * `target::String`: PDFファイルまたはPDFファイルのディレクトリ

# キーワード

  * `quiet::Bool=false`: `true`の場合、標準出力に印刷しない

# 例外

  * [`IntegrityCheckFailed`](@ref): テーブルの整合性をチェック中に別の例外がスローされました
  * [`initialize`](@ref) からの例外

# 例

```jldoctest; output = false
using PDFHighlights
using Suppressor

path_to_pdf_dir = joinpath(pathof(PDFHighlights) |> dirname |> dirname, "test", "pdf")
path_to_pdf = joinpath(path_to_pdf_dir, "TestPDF.pdf")

_file, io = mktemp()
file = _file * ".csv"
mv(_file, file)

(@capture_out(import_highlights(file, path_to_pdf)) ==
"""

    CSV: "$(basename(file))"
    PDF: "TestPDF.pdf"
    Highlights (found / added): 7 / 7

""") |> println

(@capture_out(import_highlights(file, path_to_pdf_dir)) ==
"""

    CSV: "$(basename(file))"
    Directory: "pdf"
    Highlights (found / added): 7 / 0

""") |> println

@capture_out(import_highlights(file, path_to_pdf; quiet=true)) == ""

# 出力

true
true
true
```
