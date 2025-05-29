```
html_textarea(;kwargs...)
html_textarea(children::Any, kwargs...)
html_textarea(children_maker::Function, kwargs...)
```

TextareaコンポーネントTextareaは、<textarea> HTML5要素のラッパーです。詳細な属性情報については、https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textareaを参照してください。

  * `children`（リストまたは単一のダッシュコンポーネント、文字列または数値; オプション）：このコンポーネントの子要素
  * `id`（String; オプション）：このコンポーネントのIDで、ダッシュコンポーネントをコールバックで識別するために使用されます。IDはアプリ内のすべてのコンポーネントで一意である必要があります。
  * `accessKey`（String; オプション）：要素をアクティブにしたり、フォーカスを追加するためのキーボードショートカット。
  * `aria-*`（String; オプション）：ワイルドカードaria属性
  * `autoComplete`（String; オプション）：このフォームのコントロールがデフォルトでブラウザによって自動的に値を補完されるかどうかを示します。
  * `autoFocus`（'autoFocus', 'autofocus', 'AUTOFOCUS' | Bool; オプション）：ページが読み込まれた後に要素が自動的にフォーカスされるべきです。
  * `className`（String; オプション）：共通のプロパティを持つ要素をスタイル設定するためにCSSと一緒に使用されることが多いです。
  * `cols`（String; オプション）：テキストエリアの列数を定義します。
  * `contentEditable`（String; オプション）：要素の内容が編集可能かどうかを示します。
  * `contextMenu`（String; オプション）：要素のコンテキストメニューとして機能する<menu>要素のIDを定義します。
  * `data-*`（String; オプション）：ワイルドカードデータ属性
  * `dir`（String; オプション）：テキストの方向を定義します。許可される値は、ltr（左から右）またはrtl（右から左）です。
  * `disable_n_clicks`（Bool; オプション）：Trueの場合、これはn_clicksプロパティを無効にします。これを使用して、スクリーンリーダーに干渉する可能性のあるイベントリスナーを削除します。
  * `disabled`（'disabled', 'DISABLED' | Bool; オプション）：ユーザーが要素と対話できるかどうかを示します。
  * `draggable`（String; オプション）：要素がドラッグ可能かどうかを定義します。
  * `form`（String; オプション）：要素の所有者であるフォームを示します。
  * `hidden`（'hidden', 'HIDDEN' | Bool; オプション）：与えられた要素のレンダリングを防ぎますが、子要素（例：スクリプト要素）はアクティブのままにします。
  * `inputMode`（String; オプション）：要素またはその内容を編集しているときにユーザーが入力する可能性のあるデータのタイプに関するヒントを提供します。この属性は、フォームコントロール（テキストエリア要素の値など）や、編集ホスト内の要素（例：contenteditable属性を使用）で使用できます。
  * `key`（String; オプション）：コンポーネントの一意の識別子で、コンポーネントをレンダリングする際にReact.jsのパフォーマンスを向上させるために使用されます。詳細については、https://reactjs.org/docs/lists-and-keys.htmlを参照してください。
  * `lang`（String; オプション）：要素で使用される言語を定義します。
  * `loading_state`（要素を含むリストはis*loading、prop*name、component*name - `is*loading`（Bool; オプション）：コンポーネントが読み込まれているかどうかを判断します -`prop*name`（String; オプション）：どのプロパティが読み込まれているかを保持します -`component*name`（String; オプション）：読み込まれているコンポーネントの名前を保持します; オプション）：dash-rendererからの読み込み状態オブジェクトを保持するオブジェクト
  * `maxLength`（String; オプション）：要素に許可される最大文字数を定義します。
  * `minLength`（String; オプション）：要素に許可される最小文字数を定義します。
  * `n_clicks`（オプション）：この要素がクリックされた回数を表す整数です。
  * `n_clicks_timestamp`（オプション）：n_clicksが変更された時刻（1970年以降のミリ秒）を表す整数です。これを使用して、どのボタンが最近変更されたかを判断できます。
  * `name`（String; オプション）：要素の名前。例えば、サーバーがフォーム送信時にフィールドを識別するために使用します。
  * `placeholder`（String; オプション）：フィールドに何が入力できるかについてユーザーへのヒントを提供します。
  * `readOnly`（String; オプション）：要素が編集可能かどうかを示します。
  * `required`（'required', 'REQUIRED' | Bool; オプション）：この要素が必須かどうかを示します。
  * `role`（String; オプション）：支援技術によって使用される要素の明示的な役割を定義します。
  * `rows`（String; オプション）：テキストエリアの行数を定義します。
  * `spellCheck`（String; オプション）：要素に対してスペルチェックが許可されているかどうかを示します。
  * `style`（Dict; オプション）：以前に設定されたスタイルを上書きするCSSスタイルを定義します。
  * `tabIndex`（String; オプション）：ブラウザのデフォルトのタブ順序を上書きし、代わりに指定された順序に従います。
  * `title`（String; オプション）：要素にマウスオーバーしたときにツールチップに表示されるテキスト。
  * `wrap`（String; オプション）：テキストを折り返すべきかどうかを示します。

```
