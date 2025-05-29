```
AbstractToolchain
```

`AbstractToolchain`は、ビルド機能を提供するためにダウンロードされるべきJLLのセットを表します。例えば、ほとんどのレシピで使用されるCツールチェーンや、Fortran、Go、Rustなどの他のツールチェーンがビルド環境に含まれることがあります。

すべてのツールチェーンは、以下のメソッドを定義する必要があります。

  * コンストラクタ

      * ツールのバージョンなどを設定するために使用されます。
  * toolchain_sources(toolchain)

      * このツールチェーンを実行するために必要な依存関係を表す`AbstractSource`のベクターを返します。インストールプレフィックスに対して相対的です。
  * toolchain*env(toolchain, deployed*prefix::String)

      * このツールチェーンを使用するコマンドに追加される環境変数のリストを含む辞書を返します。
  * platform(toolchain)

      * このツールチェーンが構築されたプラットフォームを返します。CToolchainの場合は`CrossPlatform`、HostToolsToolchainの場合は通常の`Platform`である可能性があります。
  * supported_platforms(::Type{toolchain})

      * このツールチェーンがターゲットとしてサポートするプラットフォームのリスト（タグなし）を返します。
