```
dash(;
        external_stylesheets,
        external_scripts,
        url_base_pathname,
        requests_pathname_prefix,
        routes_pathname_prefix,
        assets_folder,
        assets_url_path,
        assets_ignore,
        serve_locally,
        suppress_callback_exceptions,
        eager_loading ,
        meta_tags,
        index_string,
        assets_external_path,
        include_assets_files,
        show_undo_redo,
        compress,
        update_title
    )
```

Dashは分析用ウェブアプリケーションを構築するためのフレームワークです。JavaScriptは不要です。

環境変数で設定できるパラメータは、次のようにリストされます:   env: `DASH_****`   ここで提供された値は、環境変数よりも優先されます。

# 引数

  * `assets_folder::String` - ブラウザで使用する追加ファイルのための、現在の作業ディレクトリに対する相対パス。デフォルトは`'assets'`です。すべての.jsおよび.cssファイルは、`assets_ignore`で除外されない限り即座に読み込まれ、画像などの他のファイルは要求された場合に提供されます。
  * `assets_url_path::String` - アセットのローカルURLは次のようになります:       $requests_pathname_prefix * assets_url_path * "/" * asset_path$       ここで$asset_path$は$assets_folder$内のファイルへのパスです。デフォルトは$'assets'$です。
  * `assets_ignore::String` - [実験的] アセットを即座に読み込むのを省略するために$Regex$に渡す文字列としての正規表現。無視されたファイルは、特に要求された場合には依然として提供されます。これを使用して機密ファイルへのアクセスを防ぐことはできません。   :type assets_ignore: string
  * `assets_external_path::String` - [実験的] アセットを読み込むための絶対URL。       $serve_locally=false$で使用します。Dashは、Dashがインデックスできるアセットフォルダにローカルコピーを保持している場合、jsおよびcssを自動的に読み込むことができますが、外部提供はパフォーマンスを向上させ、Dashサーバーへの負荷を軽減することができます。       env: `DASH_ASSETS_EXTERNAL_PATH`
  * `include_assets_files::Bool` - [実験的] デフォルトは$true$、$false$に設定すると、アセットの即時読み込みを防ぎます。アセットは特に要求された場合には依然として提供されます。これを使用して機密ファイルへのアクセスを防ぐことはできません。       env: `DASH_INCLUDE_ASSETS_FILES`
  * `url_base_pathname::String`: アプリ全体で使用するローカルURLプレフィックス。       デフォルトは$nothing$です。`requests_pathname_prefix`と`routes_pathname_prefix`はどちらも`url_base_pathname`がデフォルトです。       env: `DASH_URL_BASE_PATHNAME`
  * `requests_pathname_prefix::String`: ファイルリクエスト用のローカルURLプレフィックス。       デフォルトは`url_base_pathname`で、`routes_pathname_prefix`で終わる必要があります。       env: `DASH_REQUESTS_PATHNAME_PREFIX`
  * `routes_pathname_prefix::String`: JSONリクエスト用のローカルURLプレフィックス。       デフォルトは$url_base_pathname$で、$'/'$で始まり、$'/'$で終わる必要があります。       env: `DASH_ROUTES_PATHNAME_PREFIX`
  * `serve_locally`: [実験的] `true`（デフォルト）の場合、アセットと依存関係（Dashおよびコンポーネントのjsおよびcss）はローカルURLから提供されます。`false`の場合、Dashは利用可能なCDNリンクを使用します。       (Dashおよびコンポーネントのjsおよびcss)はローカルURLから提供されます。       $false$の場合、利用可能なCDNリンクを使用します。
  * `meta_tags::Vector{Dict{String, String}}`: インデックスページに追加されるhtml <meta>タグ。       各辞書は1つのタグの属性と値を持つ必要があります。例:       $Dict("name"=>"description", "content" => "My App")$
  * `index_string::String`: 標準のDashインデックスページをオーバーライドします。       アプリの設定や使用されるコンポーネントに応じてさまざまなコンテンツを挿入するための正しい挿入マーカーを含む必要があります。       詳細については https://dash.plotly.com/external-resources を参照してください。
  * `external_scripts::Vector`: ページと一緒に読み込む追加のJSファイル。       各エントリは文字列（URL）または$src$（URL）を持つDict{String, String}で、オプションで$integrity$や$crossorigin$などの他の$<script>$タグ属性を持つことができます。
  * `external_stylesheets::Vector`: ページと一緒に読み込む追加のCSSファイル。       各エントリは文字列（URL）または$href$（URL）を持つDict{String, String}で、オプションで$rel$、$integrity$、$crossorigin$などの他の$<link>$タグ属性を持つことができます。
  * `suppress_callback_exceptions::Bool`: デフォルトは$false$: コールバックをチェックして、参照されたIDが存在し、プロパティが有効であることを確認します。レイアウトが動的な場合は$true$に設定して、これらのチェックをバイパスします。       env: `DASH_SUPPRESS_CALLBACK_EXCEPTIONS`
  * `prevent_initial_callbacks::Bool`: デフォルトは$false$: アプリに追加されたすべてのコールバックの$prevent_initial_call$のデフォルト値を設定します。通常、関連する出力がページに最初に追加されると、すべてのコールバックが発火します。これを個々のコールバックで無効にするには、それらの定義で$prevent_initial_call$を設定するか、ここで$true$に設定し、その場合は初期呼び出しを持ちたいコールバックに対して明示的に$false$に設定する必要があります。この設定は、後で入力が変更されたときにコールバックをトリガーすることには影響しません。
  * `show_undo_redo::Bool`: デフォルトは$false$、$true$に設定すると、アプリの状態の履歴をステップするための元に戻すおよびやり直すボタンを有効にします。
  * `compress::Bool`: デフォルトは$true$、クライアントがサポートしている場合にHTTP.jlによって提供されるファイルとデータを圧縮するためにgzipが使用されるかどうかを制御します。圧縮を完全に無効にするには$false$に設定します。
  * `update_title::String`: デフォルトは$Updating...$です。コールバックが実行されているときにdocument.title（ブラウザタブに表示されるテキスト）を構成します。document.titleを変更したくない場合や、別のコンポーネントやクライアントサイドのコールバックを通じてdocument.titleを制御したい場合は、''に設定します。
