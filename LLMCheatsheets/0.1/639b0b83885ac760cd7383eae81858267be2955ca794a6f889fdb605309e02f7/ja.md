```
summarize_file(file_info::AbstractDict; model = "gpt4o",
    special_instructions::AbstractString = "None.
```

",         cost*tracker::Union{Nothing, Threads.Atomic{<:Real}} = nothing,         verbose::Bool = true, http*kwargs::NamedTuple = NamedTuple())

GitHub リポジトリ内のファイルの内容を要約します。

# 引数

  * `file_info::AbstractDict`: GitHub API からのファイル情報。`:name` と `:download_url` フィールドが必要です。
  * `model::String`: LLM 呼び出しに使用するモデル。
  * `special_instructions::AbstractString`: AI に出力を調整させるための特別な指示。
  * `cost_tracker::Union{Nothing, Threads.Atomic{<:Real}}`: LLM 呼び出しのコストを記録するトラッカー。
  * `verbose::Bool`: 詳細な出力を印刷するかどうか。
  * `http_kwargs::NamedTuple`: `github_api` 関数に渡す追加のキーワード引数。

# 戻り値

  * `Dict`: ファイル名（`:name` フィールド）、内容（`:content` フィールド）、およびタイプ（`:type` フィールド）を含む辞書。
