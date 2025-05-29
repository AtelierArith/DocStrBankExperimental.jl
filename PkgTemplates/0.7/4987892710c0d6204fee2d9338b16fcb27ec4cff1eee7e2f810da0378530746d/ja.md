```
CompatHelper(;
    file="~/.julia/packages/PkgTemplates/MepaC/templates/github/workflows/CompatHelper.yml",
    destination="CompatHelper.yml",
    cron="0 0 * * *",
)
```

あなたのパッケージを[CompatHelper](https://github.com/bcbi/CompatHelper.jl)とGitHub Actionsを通じて統合します。

## キーワード引数

  * `file::AbstractString`: ワークフローファイルのテンプレートファイル。
  * `destination::AbstractString`: `.github/workflows`に対するワークフローファイルの宛先。
  * `cron::AbstractString`: スケジュール間隔のためのCron式。
