```
TagBot(;
    file="~/.julia/packages/PkgTemplates/MepaC/templates/github/workflows/TagBot.yml",
    destination="TagBot.yml",
    trigger="JuliaTagBot",
    token=Secret("GITHUB_TOKEN"),
    ssh=Secret("DOCUMENTER_KEY"),
    ssh_password=nothing,
    changelog=nothing,
    changelog_ignore=nothing,
    gpg=nothing,
    gpg_password=nothing,
    registry=nothing,
    branches=nothing,
    dispatch=nothing,
    dispatch_delay=nothing,
)
```

GitHubリリースサポートを[TagBot](https://github.com/JuliaRegistries/TagBot)を介して追加します。

## キーワード引数

  * `file::AbstractString`: ワークフローファイルのテンプレートファイル。
  * `destination::AbstractString`: `.github/workflows`に対するワークフローファイルの宛先。
  * `trigger::AbstractString`: カスタムレジストリのトリガーユーザーのユーザー名。
  * `token::Secret`: 使用するトークンシークレットの名前。
  * `ssh::Secret`: 使用するSSHプライベートキーシークレットの名前。
  * `ssh_password::Secret`: 使用するSSHキーのパスワードシークレットの名前。
  * `changelog::AbstractString`: カスタムチェンジログテンプレート。
  * `changelog_ignore::Vector{<:AbstractString}`: チェンジログで無視するイシュー/プルリクエストラベル。
  * `gpg::Secret`: 使用するGPGプライベートキーシークレットの名前。
  * `gpg_password::Secret`: 使用するGPGプライベートキーのパスワードシークレットの名前。
  * `registry::AbstractString`: `owner/repo`形式のカスタムレジストリ。
  * `branches::Bool`: `branches`オプションを有効にするかどうか。
  * `dispatch::Bool`: `dispatch`オプションを有効にするかどうか。
  * `dispatch_delay::Int`: ディスパッチイベントの遅延時間（分）。
