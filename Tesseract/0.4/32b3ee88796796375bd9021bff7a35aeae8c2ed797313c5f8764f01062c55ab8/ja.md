```
update_languages(
    languages::AbstractString = "eng";
    target::AbstractString = "tessdata",
    frequency::Integer = 7,
    source::GitHubProject = DATA_REPO
)::Bool
```

指定された言語のトレーニングデータファイルを更新します。ファイルの更新中にエラーが発生した場合はfalseを返します。

**引数:**

| T   | 名前        | デフォルト      | 説明                              |
|:--- |:--------- |:---------- |:------------------------------- |
| O   | languages | `eng`      | 更新する言語を"+"で区切って指定します。           |
| K   | target    | `tessdata` | データファイルを保存するディレクトリ。             |
| K   | frequency | `7`        | サーバーの更新を確認する頻度（日数）。             |
| K   | source    | ...        | トレーニングデータをダウンロードするGitHubプロジェクト。 |

**詳細:**

デフォルトでは、データファイルは現在のディレクトリの下にある「tessdata」ディレクトリに保存されます。トレーニングデータは通常、https://github.com/tesseract-ocr/tessdata_best GitHubプロジェクトからダウンロードされます。

参照: [`download_languages`](@ref)
