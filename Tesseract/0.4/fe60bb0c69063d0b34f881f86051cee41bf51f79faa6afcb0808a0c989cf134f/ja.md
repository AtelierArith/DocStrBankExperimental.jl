```
update_pdf_font(;
    target::AbstractString = "tessdata",
    frequency::Integer = 7,
    source::GitHubProject = PDF_FONT_REPO
)::Bool
```

PDFフォントファイルを更新します。これはPDFファイルを生成する際にのみ必要です。ファイルの更新中にエラーが発生した場合はfalseを返します。

**引数:**

| T   | 名前        | デフォルト      | 説明                             |
|:--- |:--------- |:---------- |:------------------------------ |
| K   | target    | `tessdata` | フォントファイルを保存するディレクトリ。           |
| K   | frequency | `7`        | サーバーでの更新を確認する頻度（日数）。           |
| K   | source    | ...        | フォントファイルをダウンロードするGitHubプロジェクト。 |

**詳細:**

デフォルトでは、データファイルは現在のディレクトリの下にある「tessdata」ディレクトリに保存されます。トレーニングデータは通常、https://github.com/tesseract-ocr/tessdata_best GitHubプロジェクトからダウンロードされます。

関連情報: [`download_pdf_font`](@ref)
