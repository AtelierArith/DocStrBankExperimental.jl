```
initconfig(; <keyword arguments>)
```

オプションで、configs 環境をオーバーライドします。

最初の [`getconfig`](@ref)、[`hasconfig`](@ref) または [`setconfig!`](@ref) の呼び出し時に自動的に呼び出されます。

一度だけ呼び出すことができます。

または、対応する `ENV` 変数 `DEPLOYMENT_KEY` または `CONFIGS_DIRECTORY` を好みに設定します。

## 引数

  * `deployment_key::String`: 意図されたデプロイメントを定義する `ENV` キー（例：本番、ステージングなど）

デフォルト: `DEPLOYMENT`

  * `configs_directory::String`: 設定定義を含むディレクトリ

プロジェクトルートに対して相対的または絶対的である可能性があります。デフォルト: `configs`
