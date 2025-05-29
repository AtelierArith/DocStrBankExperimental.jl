```
create_cheatsheet(
    repo::GitHubRepo, file_contents::AbstractVector{<:AbstractDict};
    model = "gpt4o", special_instructions::AbstractString = "None.
```

",         template::Symbol = :CheatsheetCreator,         cost*tracker::Union{Nothing, Threads.Atomic{<:Real}} = nothing,         verbose::Bool = true, save*path::Union{Nothing, String, Bool} = nothing,         http_kwargs::NamedTuple = NamedTuple())

```
create_cheatsheet(repo::GitHubRepo;
    model = "gpt4o", cost_tracker::Union{Nothing, Threads.Atomic{<:Real}} = Threads.Atomic{Float64}(0.0),
    special_instructions::AbstractString = "None.
```

",         template::Symbol = :CheatsheetCreator,         verbose::Bool = true, save*path::Union{Nothing, String} = nothing,         ntasks::Int = 0,         http*kwargs::NamedTuple = NamedTuple())

指定されたGitHubリポジトリとファイルの要約のためのチートシートを作成します。

注意: GitHub APIによってレート制限を受けている場合は、個人用アクセストークンをリクエストし、それを`ENV["GITHUB_API_KEY"]`として設定してください（リクエストの制限を1時間あたり5000に引き上げます）。

# 引数

  * `repo::GitHubRepo`: チートシートを作成するリポジトリ。
  * `file_contents::AbstractVector{<:AbstractDict}`: リポジトリ内のファイルの内容または要約。提供されない場合、リポジトリがスキャンされ、ファイルの要約が作成されます。
  * `model::String`: LLM呼び出しに使用するモデル。
  * `special_instructions::AbstractString`: AIに出力を調整させるための特別な指示。
  * `template::Symbol`: チートシート作成に使用するテンプレート。
  * `cost_tracker::Union{Nothing, Threads.Atomic{<:Real}}`: LLM呼び出しのコストを記録するためのトラッカー。
  * `verbose::Bool`: 詳細な出力を印刷するかどうか。
  * `save_path::Union{Nothing, String, Bool}`: チートシートを保存するパス。`true`の場合、チートシートは現在の作業ディレクトリ内の`llm-cheatsheets`というサブディレクトリに自動保存されます。
  * `http_kwargs::NamedTuple`: HTTPリクエストに影響を与える`github_api`関数に渡す追加のキーワード引数。
  * `ntasks::Int`: 非同期処理に使用するタスクの数。`0`の場合、タスクの数は`asyncmap`のデフォルトに設定されます。

# 戻り値

  * `String`: チートシートの内容。

```
