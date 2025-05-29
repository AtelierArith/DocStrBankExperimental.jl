```
export_directory(start_dir::String="."; kwargs...)
```

現在のフォルダー内のすべてのPlutoノートブックを再帰的に検索し、各ノートブックについて：

  * ノートブックを実行し、すべてのセルが終了するのを待つ
  * ステートオブジェクトをエクスポートする
  * ノートブックと同じ名前の.htmlファイルを作成し、以下を含む：

      * Plutoエディタを読み込むためのJSおよびCSSアセット
      * 埋め込まれたステートオブジェクト
      * 隠れたUI、バインダーボタン、ライブバインドサーバーなどの追加機能が有効

# キーワード引数

  * `Export_enabled::Bool = true`: 静的HTMLファイルを生成しますか？この設定は、スライダーサーバーを実行している場合にのみ`false`にすることができます。
  * `Export_output_dir::Union{Nothing, String} = nothing`: 生成されたHTMLファイルを書き込むフォルダー（入力フォルダー構造を保持するためにディレクトリを作成します）。デフォルト値の動作は、スライダーサーバーを実行しているか、単にエクスポートしているかによって異なります。スライダーサーバーを実行している場合は、一時ディレクトリを使用します。それ以外の場合は、`start_dir`を使用します（つまり、ノートブックファイルと同じフォルダーに各HTMLファイルを生成します）。
  * `Export_exclude::Vector{String} = String[]`: スキップするノートブックファイルのリスト。`start_dir`に対して相対的なパスを提供します。`*`ワイルドカードや他の[グロブパターン](https://en.wikipedia.org/wiki/Glob_(programming))を使用できます。
  * `Export_ignore_cache::Vector = String[]`: 常に再実行する必要があるノートブックファイルのリストで、`cache_dir`システムをスキップします。`start_dir`に対して相対的なパスを提供します。`*`ワイルドカードや他の[グロブパターン](https://en.wikipedia.org/wiki/Glob_(programming))を使用できます。
  * `Export_cache_dir::Union{Nothing, String} = nothing`: 提供された場合、このディレクトリを使用してキャッシュされたノートブックの状態を読み書きします。キャッシュはノートブックファイルのハッシュによってインデックスされますが、Plutoまたはこのエクスポートスクリプトが更新されたときにキャッシュを無効にする必要があります。https://github.com/actions/cacheとの組み合わせで便利です。例については、https://github.com/JuliaPluto/static-export-templateを参照してください。
  * `Export_baked_state::Bool = true`: ステートオブジェクトをbase64エンコードし、.htmlファイル内に書き込みます。`false`の場合、別の`.plutostate`ファイルが生成されます。別のステートファイルを使用すると、ステートファイルが読み込まれている間にPlutoで読み込みバーを表示できますが、一部の環境ではセットアップが複雑になる可能性があります。
  * `Export_baked_notebookfile::Bool = true`: .jlノートブックソースをbase64エンコードし、.htmlファイル内に書き込みます。`false`の場合、別の`.jl`ファイルが生成されるか、元のファイルが使用されます。主な違いは、HTMLファイルの「このノートブックを編集または実行 > あなたのコンピュータで」のフローにあります：別のノートブックファイル（デフォルト）を使用すると、Plutoでコピーして開くことができるURLになります。焼き付けられたノートブックファイルを使用すると、ダウンロードボタンになり、訪問者はノートブックをローカルドライブに保存する必要があり、これがより複雑になる可能性があります。
  * `Export_disable_ui::Bool = true`: Plutoのすべてのボタンとツールバーを隠して、記事のように見せます。
  * `Export_offer_binder::Bool = true`: ノートブックに「Binderで実行」ボタンを表示します。
  * `Export_binder_url::Union{Nothing, String} = nothing`: 高度な設定：右上の「Binderで実行」ボタンをクリックしたときに読み込むバインダーレポジトリのURL。デフォルト値のままにすると、自動的に設定されます。この設定は非常に高度で、`https://github.com/fonsp/pluto-on-binder/`のフォークを持っている場合にのみ意味があります（バインダーの起動を制御したい場合や、Plutoの独自のフォークを使用している場合）。その場合、設定は`"https://mybinder.org/v2/gh/fonsp/pluto-on-binder/v0.17.2"`の形式である必要があります。ここで、`fonsp/pluto-on-binder`はリポジトリの名前で、`v0.17.2`はタグまたはコミットハッシュです。
  * `Export_slider_server_url::Union{Nothing, String} = nothing`: 1) このセットアップを使用してノートブックのHTMLファイルをエクスポートしている場合、かつ2) スライダーサーバーを**別のセットアップ/コンピュータ**で実行している場合、この設定はスライダーサーバーを指すURLである必要があります。例：`"https://sliderserver.mycoolproject.org/"`。たとえば、GitHub ActionsとGitHub Pagesを使用してHTMLファイルを生成し、DigitalOceanでスライダーサーバーを使用する場合に必要です。=== 静的エクスポートとスライダーサーバーの両方に*1つ*のサーバーしかない場合、ユーザーがノートブックを直接サーバーで読む場合は、デフォルト値`nothing`が機能します：それは自動的にHTMLファイルが現在のドメインをスライダーサーバーに使用するようにします。
  * `Export_create_index::Bool = true`: 自動的に`index.html`ファイルを生成し、すべてのエクスポートされたノートブックをリストします（`index.jl`または`index.html`ファイルが既に存在しない場合のみ）。
  * `Export_create_pluto_featured_index::Union{Nothing, Bool} = nothing`: 自動生成されたインデックスページにノートブックを表示するためにPluto Featured GUIを使用し、タイトル、説明、画像などのフロントマターを使用します。デフォルトは現在`false`ですが、将来的に変更される可能性があります。明示的に`true`または`false`に設定して値を固定します。
  * `notebook_paths::Vector{String}=find_notebook_files_recursive(start_dir)`: 再帰的な保存動作を望まない場合は、これを絶対パスのベクターに設定できます。その場合、`start_dir`は無視され、`Export_output_dir`を設定する必要があります。
