```
dbc_table(;kwargs...)
dbc_table(children::Any;kwargs...)
dbc_table(children_maker::Function;kwargs...)
```

テーブルコンポーネント。HTMLテーブルにBootstrapスタイルを適用するためのコンポーネントです。`html.Table`の代わりに使用するか、`dbc.Table.from_dataframe`を使用してPandas DataFrameからテーブルを生成します。キーワード引数：

  * `children`（ダッシュコンポーネント、文字列、または数値のリストまたは単一のもの; オプション）：このコンポーネントの子要素
  * `id`（文字列; オプション）：このコンポーネントのIDで、コールバック内でダッシュコンポーネントを識別するために使用されます。IDはアプリ内のすべてのコンポーネントで一意である必要があります。
  * `bordered`（Bool; オプション）：テーブルとセルのすべての側に境界線を追加する`table-bordered`クラスを適用します。
  * `borderless`（Bool; オプション）：テーブルとセルからすべての境界線を削除する`table-borderless`クラスを適用します。
  * `className`（文字列; オプション）：**非推奨** `class_name`を代わりに使用してください。

一般的に、共通のプロパティを持つ要素のスタイルを設定するためにCSSと一緒に使用されます。

  * `class_name`（文字列; オプション）：一般的に、共通のプロパティを持つ要素のスタイルを設定するためにCSSと一緒に使用されます。
  * `color`（文字列; オプション）：テーブルの色、オプション：primary、secondary、success、info、warning、danger、

dark、light。デフォルト：secondary。

  * `dark`（Bool; オプション）：**非推奨** - 代わりにcolor="dark"を使用してください。

ダークセルの背景と明るいテキストのために`table-dark`クラスを適用します。

  * `hover`（Bool; オプション）：テーブルボディ内のテーブル行にホバー状態を有効にする`table-hover`クラスを適用します。
  * `key`（文字列; オプション）：コンポーネントの一意の識別子で、コンポーネントをレンダリングする際にReact.jsによってパフォーマンスを向上させるために使用されます。詳細についてはhttps://reactjs.org/docs/lists-and-keys.htmlを参照してください。
  * `loading_state`（オプション）：dash-rendererからのローディング状態オブジェクトを保持するオブジェクト。loading*stateは次の型を持ちます：要素'is*loading'、'prop*name'、'component*name'を含むリスト。

これらの要素は次の型を持ちます：

  * `is_loading`（Bool; オプション）：コンポーネントが読み込まれているかどうかを判断します。
  * `prop_name`（文字列; オプション）：どのプロパティが読み込まれているかを保持します。
  * `component_name`（文字列; オプション）：読み込まれているコンポーネントの名前を保持します。
  * `responsive`（Bool | 文字列; オプション）：テーブルが低いブレークポイントで水平方向にスクロールするように、Trueまたはブレークポイントの1つ'sm'、'md'、'lg'、'xl'に設定します。
  * `size`（文字列; オプション）：テーブルサイズを指定します。オプション：'sm'、'md'、'lg'
  * `striped`（Bool; オプション）：テーブルボディ内の行に「ゼブラストライプ」を適用する`table-striped`クラスを適用します。
  * `style`（辞書; オプション）：以前に設定されたスタイルを上書きするCSSスタイルを定義します。
