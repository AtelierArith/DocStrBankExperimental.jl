```
MarkdownVitepress(; repo, devbranch, devurl, kwargs...)
```

これはVitepress Markdownライターのメインエントリポイントです。

これは`Documenter.makedocs`の`format`キーワード引数に渡すことができる設定であり、Vitepressサイトを出力するようにします。

!!! tip "クイックスタート"
    `Documenter.makedocs`を呼び出す際には、デフォルトの`format=Documenter.HTML(...)`を次のように置き換えます：

    ```julia
    format=DocumenterVitepress.MarkdownVitepress(; repo = "...", devbranch = "...", devurl = "...")
    ```


## キーワード引数（設定）

  * `repo`: *必須*: ドキュメントがデプロイされるリポジトリの完全なURL。
  * `devbranch`: `master`や`main`のような開発ブランチの名前。
  * `devurl`: `dev`や`dev-branch`のような開発サイトへのURLパス。
  * `deploy_url`: ドキュメントがデプロイされるリポジトリのURL。この**必須**は完全なURLであり、**`https://`を含む**必要があります。例：`https://rafaqz.github.io/Rasters.jl`や`https://geo.makie.jl/`。
  * `description`: ウェブサイトの説明を文字列として。
  * `build_vitepress`: Vitepressサイトを構築するか、マークダウンファイルのみを出力するかを決定します。デフォルトは`true`、すなわち完全なVitepressサイトを構築します。
  * `install_npm`: Vitepressサイトを構築する前に`npm install`を実行するかどうかを決定します。デフォルトは`true`。
  * `md_output_path`: マークダウンファイルが出力されるパス。デフォルトは`$build/.documenter`。
  * `deploy_decision`: Documenter.jlからのDeployDecision。これはドキュメントをデプロイするかどうかを決定するために使用されます。オプションは：

      * `nothing`: **デフォルト**。ドキュメントをデプロイするかどうかを自動的に判断します。
      * `Documenter.DeployDecision`: 自動的な決定をオーバーライドし、渡された設定に基づいてデプロイします。

    DocumenterVitepressが自動的にデプロイに失敗した場合は、後者を使用するのが便利です。手動で構築した`Documenter.DeployDecision`構造体を渡すか、`Documenter.deploy_folder(Documenter.auto_detect_deploy_system(); repo, devbranch, devurl, push_preview)`の出力を渡すことができます。
  * `assets`: DocumenterのHTMLWriterに提供されるのと同じアセットのリスト。
  * `inventory_version`: objects.invインベントリファイルのヘッダーに書き込むバージョン文字列。これはvプレフィックスなしの有効なバージョン番号である必要があります。デフォルトはドキュメントルートの親フォルダにあるProject.tomlファイルで定義されたバージョンです。
  * `keep`: 保持すべきバージョンの粒度を設定します。オプションは:patch、:minorまたは:breaking（デフォルト）。これを使用して、開発ブランチに共存するドキュメントバージョンの数を減らすことができます。:patchでは、すべてのパッチバージョンが保存されます。:minorでは、v1.1.0、v1.1.1、v1.1.2などがv1.1として互いに上書きされます。:breakingでは、メジャーバージョンv1、v2、v3などのみが保持され、v1未満では各マイナーバージョンが保持されます。これは、これらがJuliaのSemVerの解釈においてブレイキングと見なされるためです。

## 拡張ヘルプ

`repo` kwargはドキュメントの編集リンクを設定するために使用されます。

`devbranch`と`devurl` kwargは、Vitepressが事前に期待する静的サイトのパスを設定するために使用されます。
