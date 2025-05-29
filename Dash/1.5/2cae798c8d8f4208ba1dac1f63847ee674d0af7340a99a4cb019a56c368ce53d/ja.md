```
html_th(;kwargs...)
html_th(children::Any, kwargs...)
html_th(children_maker::Function, kwargs...)
```

ThコンポーネントThは、<th> HTML5要素のラッパーです。詳細な属性情報については、https://developer.mozilla.org/en-US/docs/Web/HTML/Element/th を参照してください。

  * `children`（ダッシュコンポーネント、文字列、または数値のリストまたは単一; オプション）：このコンポーネントの子要素
  * `id`（String; オプション）：このコンポーネントのIDで、ダッシュコンポーネントをコールバックで識別するために使用されます。IDはアプリ内のすべてのコンポーネントで一意である必要があります。
  * `accessKey`（String; オプション）：要素をアクティブにしたり、フォーカスを追加するためのキーボードショートカット。
  * `aria-*`（String; オプション）：ワイルドカードaria属性
  * `className`（String; オプション）：一般的なプロパティを持つ要素をスタイルするためにCSSと共に使用されることが多いです。
  * `colSpan`（String; オプション）：colspan属性は、セルがまたがるべき列の数を定義します。
  * `contentEditable`（String; オプション）：要素の内容が編集可能かどうかを示します。
  * `contextMenu`（String; オプション）：要素のコンテキストメニューとして機能する<menu>要素のIDを定義します。
  * `data-*`（String; オプション）：ワイルドカードデータ属性
  * `dir`（String; オプション）：テキストの方向を定義します。許可される値は、ltr（左から右）またはrtl（右から左）です。
  * `disable_n_clicks`（Bool; オプション）：Trueの場合、これはn_clicksプロパティを無効にします。これは、スクリーンリーダーに干渉する可能性のあるイベントリスナーを削除するために使用します。
  * `draggable`（String; オプション）：要素がドラッグ可能かどうかを定義します。
  * `headers`（String; オプション）：この要素に適用される<th>要素のID。
  * `hidden`（'hidden', 'HIDDEN' | Bool; オプション）：指定された要素のレンダリングを防ぎますが、子要素（例：スクリプト要素）はアクティブのままにします。
  * `key`（String; オプション）：コンポーネントの一意の識別子で、コンポーネントをレンダリングする際にReact.jsによってパフォーマンスを向上させるために使用されます。詳細については、https://reactjs.org/docs/lists-and-keys.html を参照してください。
  * `lang`（String; オプション）：要素で使用される言語を定義します。
  * `loading_state`（要素を含むリストはis*loading、prop*name、component*name - `is*loading`（Bool; オプション）：コンポーネントが読み込まれているかどうかを判断します -`prop*name`（String; オプション）：どのプロパティが読み込まれているかを保持します -`component*name`（String; オプション）：読み込まれているコンポーネントの名前を保持します; オプション）：dash-rendererからの読み込み状態オブジェクトを保持するオブジェクト
  * `n_clicks`（オプション）：この要素がクリックされた回数を表す整数。
  * `n_clicks_timestamp`（オプション）：n_clicksが変更された時刻（1970年からのミリ秒）を表す整数です。これを使用して、どのボタンが最近変更されたかを判断できます。
  * `role`（String; オプション）：支援技術によって使用される要素の明示的な役割を定義します。
  * `rowSpan`（String; オプション）：テーブルセルがまたがるべき行の数を定義します。
  * `scope`（String; オプション）：ヘッダーのテスト（th要素で定義された）が関連するセルを定義します。
  * `spellCheck`（String; オプション）：要素に対してスペルチェックが許可されているかどうかを示します。
  * `style`（Dict; オプション）：以前に設定されたスタイルを上書きするCSSスタイルを定義します。
  * `tabIndex`（String; オプション）：ブラウザのデフォルトのタブ順序を上書きし、代わりに指定された順序に従います。
  * `title`（String; オプション）：要素にマウスオーバーしたときにツールチップに表示されるテキスト。

```
