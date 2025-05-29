```
dbc_navitem(;kwargs...)
dbc_navitem(children::Any;kwargs...)
dbc_navitem(children_maker::Function;kwargs...)
```

NavItemコンポーネント。`Nav`内に単一のアイテムを作成します。キーワード引数：

  * `children`（リストまたは単一のダッシュコンポーネント、文字列または数値; オプション）：このコンポーネントの子要素
  * `id`（String; オプション）：このコンポーネントのIDで、ダッシュコンポーネントをコールバックで識別するために使用されます。IDはアプリ内のすべてのコンポーネントで一意である必要があります。
  * `className`（String; オプション）：**非推奨** `class_name`を代わりに使用してください。

一般的に、共通のプロパティを持つ要素のスタイルを設定するためにCSSと一緒に使用されます。

  * `class_name`（String; オプション）：一般的に、共通のプロパティを持つ要素のスタイルを設定するためにCSSと一緒に使用されます。
  * `key`（String; オプション）：コンポーネントの一意の識別子で、コンポーネントをレンダリングする際にReact.jsによってパフォーマンスを向上させるために使用されます。詳細については、https://reactjs.org/docs/lists-and-keys.htmlを参照してください。
  * `loading_state`（オプション）：dash-rendererからのローディング状態オブジェクトを保持するオブジェクト。loading*stateは次の型を持ちます：要素'is*loading'、'prop*name'、'component*name'を含むリスト。

これらの要素は次の型を持ちます：

  * `is_loading`（Bool; オプション）：コンポーネントがロード中かどうかを判断します
  * `prop_name`（String; オプション）：どのプロパティがロード中であるかを保持します
  * `component_name`（String; オプション）：ロード中のコンポーネントの名前を保持します
  * `style`（Dict; オプション）：以前に設定されたスタイルを上書きするCSSスタイルを定義します。
