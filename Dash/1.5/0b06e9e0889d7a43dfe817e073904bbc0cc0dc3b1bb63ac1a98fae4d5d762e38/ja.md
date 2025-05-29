```
html_button(;kwargs...)
html_button(children::Any, kwargs...)
html_button(children_maker::Function, kwargs...)
```

ButtonコンポーネントButtonは、<button> HTML5要素のラッパーです。詳細な属性情報については、https://developer.mozilla.org/en-US/docs/Web/HTML/Element/button を参照してください。

  * `children`（リストまたは単一のダッシュコンポーネント、文字列または数値; オプション）：このコンポーネントの子要素
  * `id`（String; オプション）：このコンポーネントのIDで、ダッシュコンポーネントをコールバックで識別するために使用されます。IDはアプリ内のすべてのコンポーネントで一意である必要があります。
  * `accessKey`（String; オプション）：要素をアクティブにしたり、フォーカスを追加するためのキーボードショートカット。
  * `aria-*`（String; オプション）：ワイルドカードaria属性
  * `autoFocus`（'autoFocus', 'autofocus', 'AUTOFOCUS' | Bool; オプション）：ページが読み込まれた後に自動的にフォーカスされるべき要素。
  * `className`（String; オプション）：一般的なプロパティで要素をスタイルするためにCSSと一緒に使用されることが多い。
  * `contentEditable`（String; オプション）：要素の内容が編集可能かどうかを示します。
  * `contextMenu`（String; オプション）：要素のコンテキストメニューとして機能する<menu>要素のIDを定義します。
  * `data-*`（String; オプション）：ワイルドカードデータ属性
  * `dir`（String; オプション）：テキストの方向を定義します。許可される値は、ltr（左から右）またはrtl（右から左）です。
  * `disable_n_clicks`（Bool; オプション）：Trueの場合、これはn_clicksプロパティを無効にします。これを使用して、スクリーンリーダーに干渉する可能性のあるイベントリスナーを削除します。
  * `disabled`（'disabled', 'DISABLED' | Bool; オプション）：ユーザーが要素と対話できるかどうかを示します。
  * `draggable`（String; オプション）：要素がドラッグ可能かどうかを定義します。
  * `form`（String; オプション）：要素の所有者であるフォームを示します。
  * `formAction`（String; オプション）：要素のアクションを示し、<form>で定義されたアクションを上書きします。
  * `formEncType`（String; オプション）：ボタン/入力が送信ボタン（例：type="submit"）の場合、この属性はフォーム送信中に使用するエンコーディングタイプを設定します。この属性が指定されている場合、ボタンのフォーム所有者のenctype属性を上書きします。
  * `formMethod`（String; オプション）：ボタン/入力が送信ボタン（例：type="submit"）の場合、この属性はフォーム送信中に使用する送信方法（GET、POSTなど）を設定します。この属性が指定されている場合、ボタンのフォーム所有者のmethod属性を上書きします。
  * `formNoValidate`（'formNoValidate', 'formnovalidate', 'FORMNOVALIDATE' | Bool; オプション）：ボタン/入力が送信ボタン（例：type="submit"）の場合、このブール属性は、フォームが送信されるときに検証されないことを指定します。この属性が指定されている場合、ボタンのフォーム所有者のnovalidate属性を上書きします。
  * `formTarget`（String; オプション）：ボタン/入力が送信ボタン（例：type="submit"）の場合、この属性は、フォーム送信後に受信した応答を表示するブラウジングコンテキスト（たとえば、タブ、ウィンドウ、またはインラインフレーム）を指定します。この属性が指定されている場合、ボタンのフォーム所有者のtarget属性を上書きします。
  * `hidden`（'hidden', 'HIDDEN' | Bool; オプション）：指定された要素のレンダリングを防ぎ、子要素（例：スクリプト要素）をアクティブに保ちます。
  * `key`（String; オプション）：コンポーネントの一意の識別子で、コンポーネントをレンダリングする際にReact.jsによってパフォーマンスを向上させるために使用されます。詳細については、https://reactjs.org/docs/lists-and-keys.html を参照してください。
  * `lang`（String; オプション）：要素で使用される言語を定義します。
  * `loading_state`（要素を含むリストはis*loading、prop*name、component*name - `is*loading`（Bool; オプション）：コンポーネントが読み込まれているかどうかを判断します -`prop*name`（String; オプション）：どのプロパティが読み込まれているかを保持します -`component*name`（String; オプション）：読み込まれているコンポーネントの名前を保持します; オプション）：dash-rendererからの読み込み状態オブジェクトを保持するオブジェクト
  * `n_clicks`（オプション）：この要素がクリックされた回数を表す整数です。
  * `n_clicks_timestamp`（オプション）：n_clicksが変更された時刻（1970年以降のミリ秒）を表す整数です。これを使用して、どのボタンが最近変更されたかを判断できます。
  * `name`（String; オプション）：要素の名前。たとえば、サーバーがフォーム送信でフィールドを識別するために使用します。
  * `role`（String; オプション）：支援技術で使用するための要素の明示的な役割を定義します。
  * `spellCheck`（String; オプション）：要素に対してスペルチェックが許可されているかどうかを示します。
  * `style`（Dict; オプション）：以前に設定されたスタイルを上書きするCSSスタイルを定義します。
  * `tabIndex`（String; オプション）：ブラウザのデフォルトのタブ順序を上書きし、代わりに指定された順序に従います。
  * `title`（String; オプション）：要素にマウスをホバーしたときにツールチップに表示されるテキスト。
  * `type`（String; オプション）：要素のタイプを定義します。
  * `value`（String; オプション）：ページ読み込み時に要素に表示されるデフォルト値を定義します。
