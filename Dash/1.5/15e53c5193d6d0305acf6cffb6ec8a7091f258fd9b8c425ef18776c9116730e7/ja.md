```
html_form(;kwargs...)
html_form(children::Any, kwargs...)
html_form(children_maker::Function, kwargs...)
```

FormコンポーネントFormは、<form> HTML5要素のラッパーです。詳細な属性情報については、https://developer.mozilla.org/en-US/docs/Web/HTML/Element/form を参照してください。

  * `children`（ダッシュコンポーネント、文字列、または数値のリストまたは単一; オプション）：このコンポーネントの子要素
  * `id`（String; オプション）：このコンポーネントのIDで、ダッシュコンポーネントをコールバックで識別するために使用されます。IDはアプリ内のすべてのコンポーネントで一意である必要があります。
  * `accept`（String; オプション）：サーバーが受け入れるタイプのリスト、通常はファイルタイプ。
  * `acceptCharset`（String; オプション）：サポートされている文字セットのリスト。
  * `accessKey`（String; オプション）：要素をアクティブにしたり、フォーカスを追加するためのキーボードショートカット。
  * `action`（String; オプション）：フォームを介して送信された情報を処理するプログラムのURI。
  * `aria-*`（String; オプション）：ワイルドカードaria属性
  * `autoComplete`（String; オプション）：このフォーム内のコントロールがデフォルトでブラウザによって自動的に値を補完されるかどうかを示します。
  * `className`（String; オプション）：共通のプロパティを持つ要素をスタイル設定するためにCSSと共に使用されることが多いです。
  * `contentEditable`（String; オプション）：要素の内容が編集可能かどうかを示します。
  * `contextMenu`（String; オプション）：要素のコンテキストメニューとして機能する<menu>要素のIDを定義します。
  * `data-*`（String; オプション）：ワイルドカードデータ属性
  * `dir`（String; オプション）：テキストの方向を定義します。許可される値は、ltr（左から右）またはrtl（右から左）です。
  * `disable_n_clicks`（Bool; オプション）：Trueの場合、これはn_clicksプロパティを無効にします。これを使用して、スクリーンリーダーに干渉する可能性のあるイベントリスナーを削除します。
  * `draggable`（String; オプション）：要素がドラッグ可能かどうかを定義します。
  * `encType`（String; オプション）：メソッドがPOSTのときのフォームデータのコンテンツタイプを定義します。
  * `hidden`（'hidden', 'HIDDEN' | Bool; オプション）：指定された要素のレンダリングを防ぎますが、子要素（例：スクリプト要素）はアクティブのままにします。
  * `key`（String; オプション）：コンポーネントの一意の識別子で、コンポーネントをレンダリングする際にReact.jsによってパフォーマンスを向上させるために使用されます。詳細については、https://reactjs.org/docs/lists-and-keys.html を参照してください。
  * `lang`（String; オプション）：要素で使用される言語を定義します。
  * `loading_state`（要素を含むリストはis*loading、prop*name、component*name - `is*loading`（Bool; オプション）：コンポーネントが読み込まれているかどうかを判断します -`prop*name`（String; オプション）：どのプロパティが読み込まれているかを保持します -`component*name`（String; オプション）：読み込まれているコンポーネントの名前を保持します; オプション）：dash-rendererからの読み込み状態オブジェクトを保持するオブジェクト
  * `method`（String; オプション）：フォームを送信する際に使用するHTTPメソッドを定義します。GET（デフォルト）またはPOSTを使用できます。
  * `n_clicks`（オプション）：この要素がクリックされた回数を表す整数です。
  * `n_clicks_timestamp`（オプション）：n_clicksが変更された時刻（1970年以降のミリ秒）を表す整数です。これを使用して、最も最近変更されたボタンを特定できます。
  * `name`（String; オプション）：要素の名前。例えば、サーバーがフォーム送信のフィールドを識別するために使用します。
  * `noValidate`（'noValidate', 'novalidate', 'NOVALIDATE' | Bool; オプション）：この属性は、フォームが送信時に検証されないことを示します。
  * `role`（String; オプション）：支援技術によって使用される要素の明示的な役割を定義します。
  * `spellCheck`（String; オプション）：要素に対してスペルチェックが許可されているかどうかを示します。
  * `style`（Dict; オプション）：以前に設定されたスタイルを上書きするCSSスタイルを定義します。
  * `tabIndex`（String; オプション）：ブラウザのデフォルトのタブ順序を上書きし、代わりに指定された順序に従います。
  * `target`（String; オプション）：リンクされたドキュメントを開く場所（<a>要素の場合）または受信した応答を表示する場所（<form>要素の場合）を指定します。
  * `title`（String; オプション）：要素にマウスをホバーしたときにツールチップに表示されるテキスト。
