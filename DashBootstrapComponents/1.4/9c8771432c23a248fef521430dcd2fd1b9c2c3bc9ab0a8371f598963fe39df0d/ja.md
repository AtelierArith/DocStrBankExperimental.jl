```
dbc_row(;kwargs...)
dbc_row(children::Any;kwargs...)
dbc_row(children_maker::Function;kwargs...)
```

行コンポーネント。RowはBootstrapのコアレイアウトコンポーネントの1つです。レイアウトを列の行のシリーズとして構築します。Rowには、子要素の垂直および水平方向の配置を制御するための引数や、列間の間隔を設定するための引数があります。キーワード引数：

  * `children`（リストまたは単一のダッシュコンポーネント、文字列または数値; オプション）：このコンポーネントの子要素
  * `id`（文字列; オプション）：このコンポーネントのIDで、ダッシュコンポーネントをコールバックで識別するために使用されます。IDはアプリ内のすべてのコンポーネントで一意である必要があります。
  * `align`（値は：'start'、'center'、'end'、'stretch'、'baseline'; オプション）：この行の列の垂直配置を設定します。オプションは'start'、'center'、'end'、'stretch'、および'baseline'です。
  * `className`（文字列; オプション）：**非推奨** `class_name`を代わりに使用してください。

一般的に、共通のプロパティを持つ要素のスタイルを設定するためにCSSと一緒に使用されます。

  * `class_name`（文字列; オプション）：一般的に、共通のプロパティを持つ要素のスタイルを設定するためにCSSと一緒に使用されます。
  * `justify`（値は：'start'、'center'、'end'、'around'、'between'、'evenly'; オプション）：この行の列の水平方向の間隔と配置を設定します。オプションは'start'、'center'、'end'、'around'、および'between'です。
  * `key`（文字列; オプション）：コンポーネントの一意の識別子で、React.jsがコンポーネントをレンダリングする際のパフォーマンスを向上させるために使用されます。詳細については、https://reactjs.org/docs/lists-and-keys.htmlを参照してください。
  * `loading_state`（オプション）：dash-rendererからのローディング状態オブジェクトを保持するオブジェクト。loading*stateは次のタイプを持ちます：要素'is*loading'、'prop*name'、'component*name'を含むリスト。

これらの要素は次のタイプを持ちます：

  * `is_loading`（Bool; オプション）：コンポーネントがロード中かどうかを判断します
  * `prop_name`（文字列; オプション）：どのプロパティがロード中かを保持します
  * `component_name`（文字列; オプション）：ロード中のコンポーネントの名前を保持します
  * `style`（辞書; オプション）：以前に設定されたスタイルを上書きするCSSスタイルを定義します。
