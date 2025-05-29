**BaseDirs**

このモジュールは、ファイルの適切な場所を特定するためのユーティリティを提供します。

[`User`](@ref BaseDirs.User) および [`System`](BaseDirs.System) サブモジュールは、いくつかのアクセサ関数を提供しています。

また、[`data`](@ref BaseDirs.data)、[`config`](@ref BaseDirs.config)、[`fonts`](@ref BaseDirs.fonts)、および [`applications`](@ref BaseDirs.applications) という4つの組み合わせたアクセサ関数も定義されています。これらは、すべての関連するユーザーおよびシステムディレクトリのリストを提供します。

便利なことに、ユーザー固有の3つのアクセサ [`cache`](@ref BaseDirs.User.cache)、[`runtime`](@ref BaseDirs.User.runtime)、および [`state`](@ref BaseDirs.User.state) は、`BaseDirs` の下で利用可能です。これらは、混同される可能性のある `System` の同等物がないためです。

適切なプロジェクトパスを生成する方法については、[`BaseDirs.Project`](@ref BaseDirs.Project) を参照してください。

!!! note
    これは本質的に、XDG (Cross-Desktop Group) ディレクトリ仕様の実装であり、クロスプラットフォームのために Windows および MacOS の類似物があります。より具体的には、これは以下のハイブリッドです：

      * Linux における [*XDG base directory*](https://standards.freedesktop.org/basedir-spec/basedir-spec-latest.html) および [*XDG user directory*](https://www.freedesktop.org/wiki/Software/xdg-user-dirs/) 仕様
      * Windows における [*Known Folder*](https://msdn.microsoft.com/en-us/library/windows/desktop/dd378457.aspx) API
      * macOS における [*Standard Directories*](https://developer.apple.com/library/content/documentation/FileManagement/Conceptual/FileSystemProgrammingGuide/FileSystemOverview/FileSystemOverview.html#//apple_ref/doc/uid/TP40010672-CH2-SW6) ガイドライン


# 適切なディレクトリに関するガイドライン

  * **Runtime** データは *揮発性* であり、現在のユーザーセッションにのみ関連します。ユーザー固有であり、必須ではありません。例えば：ソケット、名前付きパイプ、またはロックファイル。
  * **Cache** データは必須ではなく、*データ損失なし* に再作成できます。例えば：サムネイル、コンパイルされたバイトコード、フォントパス、またはその他のキャッシュデータ。
  * **State** データはアプリケーションの状態に関連し、*セッション* をまたいで持続する必要がありますが、バックアップする必要はありません。例えば：ログ、最近開いたファイル、またはその他のセッションデータ。
  * **Config** データはアプリケーションの動作に対するユーザー固有のカスタマイズです。例えば：テーマ設定、カスタムキーバインディング、メディアの設定、またはその他の構成。
  * **Data** コンテンツは一般的なアプリケーションデータに使用されるべきです。例えば：セーブゲームの進行状況、ライブラリのメタデータ、テンプレート、またはその他のユーザー固有/ユーザー生成データ。
  * **Bin** データは、ユーザーによって実行されることを意図した実行可能ファイルです。

バックアップに含めたい重要な情報は、**config** と **data** に分けて保存するべきです。**state** の情報はあれば良いですが、必須ではありません。
