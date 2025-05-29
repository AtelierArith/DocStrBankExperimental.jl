```
RegisterAction(;
    file="~/.julia/packages/PkgTemplates/MepaC/templates/github/workflows/Register.yml",
    destination="Register.yml",
    prompt="Version to register or component to bump",
)
```

GitHub Actions ワークフローを追加して、ワークフローディスパッチを介して一般的なレジストリにパッケージを登録します。詳細については[こちら](https://github.com/julia-actions/RegisterAction)を参照してください。

## キーワード引数

  * `file::AbstractString`: ワークフローファイルのテンプレートファイル。
  * `destination::AbstractString`: `.github/workflows`に対するワークフローファイルの宛先。
  * `prompt::AbstractString`: ワークフローディスパッチのプロンプト。
