```
dbc_popoverbody(;kwargs...)
dbc_popoverbody(children::Any;kwargs...)
dbc_popoverbody(children_maker::Function;kwargs...)
```

PopoverBodyコンポーネント。`Popover`のボディ（すなわちメインコンテンツ）をラップするためのコンポーネント。キーワード引数：

  * `children`（ダッシュコンポーネント、文字列、または数値のリストまたは単一; オプション）：このコンポーネントの子要素
  * `id`（文字列; オプション）：コールバックでダッシュコンポーネントを識別するために使用されるこのコンポーネントのID。IDはアプリ内のすべてのコンポーネントで一意である必要があります。
  * `className`（文字列; オプション）：**非推奨** `class_name`を代わりに使用してください。

一般的に、共通のプロパティを持つ要素のスタイルを設定するためにCSSと一緒に使用されます。

  * `class_name`（文字列; オプション）：一般的に、共通のプロパティを持つ要素のスタイルを設定するためにCSSと一緒に使用されます。
  * `key`（文字列; オプション）：コンポーネントの一意の識別子で、コンポーネントをレンダリングする際にReact.jsによってパフォーマンスを向上させるために使用されます。詳細についてはhttps://reactjs.org/docs/lists-and-keys.htmlを参照してください。
  * `loading_state`（オプション）：dash-rendererからのローディング状態オブジェクトを保持するオブジェクト。loading*stateは次の型を持ちます：要素'is*loading'、'prop*name'、'component*name'を含むリスト。

これらの要素は次の型を持ちます：

  * `is_loading`（Bool; オプション）：コンポーネントがロード中かどうかを判断します。
  * `prop_name`（文字列; オプション）：どのプロパティがロード中であるかを保持します。
  * `component_name`（文字列; オプション）：ロード中のコンポーネントの名前を保持します。
  * `style`（辞書; オプション）：以前に設定されたスタイルを上書きするCSSスタイルを定義します。
  * `tag`（文字列; オプション）：PopoverBodyに使用するHTMLタグ、デフォルト：div
