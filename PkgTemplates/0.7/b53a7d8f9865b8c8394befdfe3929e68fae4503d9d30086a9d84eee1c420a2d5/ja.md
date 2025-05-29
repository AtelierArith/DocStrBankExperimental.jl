```
Dependabot(; file="~/.julia/packages/PkgTemplates/MepaC/templates/github/dependabot.yml")
```

Dependabotを設定して、GitHub Actionsが更新できるたびにPRを作成します。これは、Juliaパッケージの依存関係に対して同じ作業を行う[`CompatHelper`](@ref)に非常に似ています。

!!! note "GitHub Actions専用"
    現在、このプラグインはGitHub ActionsパッケージエコシステムのためにのみDependabotを設定するように構成されています。たとえば、`uses: actions/checkout@v3`のようなGitHub Actionsが`uses: actions/checkout@v4`に更新できるときにPRを作成します。他のパッケージエコシステムを更新するためにDependabotを設定したい場合は、結果のファイルを自分で修正してください。


## キーワード引数

  * `file::AbstractString`: `dependabot.yml`のテンプレートファイル。
