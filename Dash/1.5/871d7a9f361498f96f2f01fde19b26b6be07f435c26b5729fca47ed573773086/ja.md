```
html_script(;kwargs...)
html_script(children::Any, kwargs...)
html_script(children_maker::Function, kwargs...)
```

ScriptコンポーネントScriptは、<script> HTML5要素のラッパーです。

注意: <script>は完全性のために含まれていますが、<script>要素にJavaScriptコードを提供しても実行することはできません。この目的にはクライアントサイドコールバックを使用してください。

詳細な属性情報については、https://developer.mozilla.org/en-US/docs/Web/HTML/Element/script を参照してください。

  * `children`（リストまたは単一のダッシュコンポーネント、文字列または数値; オプション）: このコンポーネントの子要素
  * `id`（String; オプション）: このコンポーネントのIDで、ダッシュコンポーネントをコールバックで識別するために使用されます。IDはアプリ内のすべてのコンポーネントで一意である必要があります。
  * `accessKey`（String; オプション）: 要素をアクティブにしたり、フォーカスを追加するためのキーボードショートカット。
  * `aria-*`（String; オプション）: ワイルドカードaria属性
  * `async`（'async', 'ASYNC' | Bool; オプション）: スクリプトを非同期に実行します。
  * `charSet`（String; オプション）: ページまたはスクリプトの文字エンコーディングを宣言します。
  * `className`（String; オプション）: 一般的なプロパティを持つ要素をスタイルするためにCSSと共に使用されることが多いです。
  * `contentEditable`（String; オプション）: 要素の内容が編集可能かどうかを示します。
  * `contextMenu`（String; オプション）: 要素のコンテキストメニューとして機能する<menu>要素のIDを定義します。
  * `crossOrigin`（String; オプション）: 要素がクロスオリジンリクエストをどのように処理するか
  * `data-*`（String; オプション）: ワイルドカードデータ属性
  * `defer`（'defer', 'DEFER' | Bool; オプション）: スクリプトがページの解析後に実行されるべきであることを示します。
  * `dir`（String; オプション）: テキストの方向を定義します。許可される値は、ltr（左から右）またはrtl（右から左）です。
  * `disable_n_clicks`（Bool; オプション）: Trueの場合、これはn_clicksプロパティを無効にします。これを使用して、スクリーンリーダーに干渉する可能性のあるイベントリスナーを削除します。
  * `draggable`（String; オプション）: 要素がドラッグ可能かどうかを定義します。
  * `hidden`（'hidden', 'HIDDEN' | Bool; オプション）: 指定された要素のレンダリングを防ぎますが、子要素（例: スクリプト要素）はアクティブのままにします。
  * `integrity`（String; オプション）: ブラウザが取得したものを検証できるようにするサブリソース整合性値を指定します。
  * `key`（String; オプション）: コンポーネントの一意の識別子で、コンポーネントをレンダリングする際にReact.jsによってパフォーマンスを向上させるために使用されます。詳細については、https://reactjs.org/docs/lists-and-keys.html を参照してください。
  * `lang`（String; オプション）: 要素で使用される言語を定義します。
  * `loading_state`（要素を含むリストは*loading、prop*name、component*name - `is*loading`（Bool; オプション）: コンポーネントが読み込まれているかどうかを判断します -`prop*name`（String; オプション）: どのプロパティが読み込まれているかを保持します -`component*name`（String; オプション）: 読み込まれているコンポーネントの名前を保持します; オプション）: dash-rendererからの読み込み状態オブジェクトを保持するオブジェクト
  * `n_clicks`（オプション）: この要素がクリックされた回数を表す整数です。
  * `n_clicks_timestamp`（オプション）: n_clicksが変更された時刻（1970年からのミリ秒）を表す整数です。これを使用して、どのボタンが最近変更されたかを判断できます。
  * `referrerPolicy`（String; オプション）: リソースを取得する際に送信されるリファラーを指定します。
  * `role`（String; オプション）: 補助技術によって使用される要素の明示的な役割を定義します。
  * `spellCheck`（String; オプション）: 要素に対してスペルチェックが許可されているかどうかを示します。
  * `src`（String; オプション）: 埋め込み可能なコンテンツのURL。
  * `style`（Dict; オプション）: 以前に設定されたスタイルを上書きするCSSスタイルを定義します。
  * `tabIndex`（String; オプション）: ブラウザのデフォルトのタブ順序を上書きし、代わりに指定された順序に従います。
  * `title`（String; オプション）: 要素にマウスオーバーしたときにツールチップに表示されるテキスト。
  * `type`（String; オプション）: 要素のタイプを定義します。
