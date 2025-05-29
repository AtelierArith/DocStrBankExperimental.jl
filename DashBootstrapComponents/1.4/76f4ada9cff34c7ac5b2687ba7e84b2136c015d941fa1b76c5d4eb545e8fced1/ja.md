```
dbc_formtext(;kwargs...)
dbc_formtext(children::Any;kwargs...)
dbc_formtext(children_maker::Function;kwargs...)
```

フォームテキストコンポーネント。入力コンポーネントの下に説明テキストを追加します。キーワード引数：

  * `children`（リストまたは単一のダッシュコンポーネント、文字列または数値; オプション）：このコンポーネントの子要素
  * `id`（文字列; オプション）：このコンポーネントのIDで、ダッシュコンポーネントを識別するために使用されます

コールバック内で。IDはアプリ内のすべてのコンポーネントで一意である必要があります。

  * `className`（文字列; オプション）：**非推奨** `class_name`を代わりに使用してください。

一般的に、共通のプロパティを持つ要素のスタイルを設定するためにCSSと一緒に使用されます。

  * `class_name`（文字列; オプション）：一般的に、共通のプロパティを持つ要素のスタイルを設定するためにCSSと一緒に使用されます。
  * `color`（文字列; オプション）：テキストの色、オプション：primary、secondary、success、warning、danger、info、

muted、light、dark、body、white、black-50、white-50またはお好みの有効なCSSカラー（例：16進数コード、10進数コード、またはCSSカラー名）。

  * `key`（文字列; オプション）：コンポーネントの一意の識別子で、コンポーネントのレンダリング時にReact.jsによるパフォーマンスを向上させるために使用されます。詳細については、https://reactjs.org/docs/lists-and-keys.htmlを参照してください。
  * `loading_state`（オプション）：dash-rendererからのローディング状態オブジェクトを保持するオブジェクト。loading*stateは次の型を持ちます：要素'is*loading'、'prop*name'、'component*name'を含むリスト。

これらの要素は次の型を持ちます：

  * `is_loading`（Bool; オプション）：コンポーネントがロード中かどうかを判断します
  * `prop_name`（文字列; オプション）：どのプロパティがロード中かを保持します
  * `component_name`（文字列; オプション）：ロード中のコンポーネントの名前を保持します
  * `style`（辞書; オプション）：以前に設定されたスタイルを上書きするCSSスタイルを定義します。
