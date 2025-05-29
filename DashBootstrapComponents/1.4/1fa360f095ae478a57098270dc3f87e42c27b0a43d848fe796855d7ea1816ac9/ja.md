```
dbc_listgroup(;kwargs...)
dbc_listgroup(children::Any;kwargs...)
dbc_listgroup(children_maker::Function;kwargs...)
```

ListGroupコンポーネント。Bootstrapのリストグループは、一連のコンテンツを表示するための柔軟な方法です。`ListGroupItem`、`ListGroupItemHeading`、および`ListGroupItemText`と組み合わせて使用します。キーワード引数：

  * `children`（リストまたは単一のダッシュコンポーネント、文字列または数値; オプション）：このコンポーネントの子要素
  * `id`（String; オプション）：このコンポーネントのIDで、ダッシュコンポーネントを識別するために使用されます

コールバック内で。IDはアプリ内のすべてのコンポーネントで一意である必要があります。

  * `className`（String; オプション）：**非推奨** `class_name`を代わりに使用してください。

一般的に、共通のプロパティを持つ要素のスタイルを設定するためにCSSと一緒に使用されます。

  * `class_name`（String; オプション）：一般的に、共通のプロパティを持つ要素のスタイルを設定するためにCSSと一緒に使用されます。
  * `flush`（Bool; オプション）：Trueの場合、`list-group-flush`クラスが適用され、リストグループからいくつかの境界線と角の丸みが削除されます

親コンテナ（例：カード）内でエッジからエッジに描画できるようにします。

  * `horizontal`（Bool | String; オプション）：水平リストグループの場合はTrueに設定するか、ブレークポイントの1つを文字列として指定します

そのブレークポイント以上で水平なリストグループになります。

水平リストグループはフラッシュリストグループと組み合わせることはできないため、フラッシュがTrueの場合、水平は効果がありません。

  * `key`（String; オプション）：コンポーネントの一意の識別子で、コンポーネントをレンダリングする際にReact.jsのパフォーマンスを向上させるために使用されます。詳細については、https://reactjs.org/docs/lists-and-keys.htmlを参照してください。
  * `loading_state`（オプション）：dash-rendererからのローディング状態オブジェクトを保持するオブジェクト。loading*stateは次のタイプを持ちます：要素'is*loading'、'prop*name'、'component*name'を含むリスト。

これらの要素は次のタイプを持ちます：

  * `is_loading`（Bool; オプション）：コンポーネントが読み込まれているかどうかを判断します
  * `prop_name`（String; オプション）：どのプロパティが読み込まれているかを保持します
  * `component_name`（String; オプション）：読み込まれているコンポーネントの名前を保持します
  * `numbered`（Bool; オプション）：番号付きリストアイテムを生成します。
  * `style`（Dict; オプション）：以前に設定されたスタイルを上書きするCSSスタイルを定義します。
  * `tag`（String; オプション）：リストに使用するHTMLタグ、デフォルト：ul
