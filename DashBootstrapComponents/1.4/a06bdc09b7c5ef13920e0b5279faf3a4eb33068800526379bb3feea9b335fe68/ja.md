```
dbc_listgroupitem(;kwargs...)
dbc_listgroupitem(children::Any;kwargs...)
dbc_listgroupitem(children_maker::Function;kwargs...)
```

`ListGroupItem` コンポーネント。`ListGroup` 内に単一のアイテムを作成します。キーワード引数：

  * `children`（リストまたは単一のダッシュコンポーネント、文字列または数値; オプション）：このコンポーネントの子要素
  * `id`（String; オプション）：このコンポーネントのIDで、ダッシュコンポーネントを識別するために使用されます。

コールバック内で。IDはアプリ内のすべてのコンポーネントで一意である必要があります。

  * `action`（Bool; オプション）：ホバーアニメーションなどのために list-group-item-action クラスを適用します。
  * `active`（Bool; オプション）：アイテムにアクティブスタイルを適用します。
  * `className`（String; オプション）：**非推奨** `class_name` を代わりに使用してください。

一般的に、共通のプロパティを持つ要素のスタイルを設定するために CSS と一緒に使用されます。

  * `class_name`（String; オプション）：一般的に、共通のプロパティを持つ要素のスタイルを設定するために CSS と一緒に使用されます。
  * `color`（String; オプション）：アイテムの色、オプション：primary、secondary、success、info、warning、

danger、またはお好みの有効な CSS 色（例：16進数コード、10進数コード、または CSS 色名）デフォルト：secondary

  * `disabled`（Bool; オプション）：アイテムに無効スタイルを適用します。
  * `external_link`（Bool; オプション）：true の場合、ブラウザはこれを外部リンクとして扱い、

新しい場所でページをリフレッシュします。false の場合、これはページのリフレッシュをトリガーせずに単に場所を変更します。たとえば、dcc.Location を監視している場合に使用します。絶対 URL の場合はデフォルトで true で、それ以外は false です。

  * `href`（String; オプション）：リストグループアイテムをリンクにするために URL（相対または絶対）を渡します。
  * `key`（String; オプション）：コンポーネントの一意の識別子で、コンポーネントをレンダリングする際に React.js によってパフォーマンスを向上させるために使用されます。詳細については https://reactjs.org/docs/lists-and-keys.html を参照してください。
  * `loading_state`（オプション）：dash-renderer からのローディング状態オブジェクトを保持するオブジェクト。loading*state は次の型を持ちます：要素 'is*loading'、'prop*name'、'component*name' を含むリスト。

これらの要素は次の型を持ちます：

  * `is_loading`（Bool; オプション）：コンポーネントがロード中かどうかを判断します。
  * `prop_name`（String; オプション）：どのプロパティがロード中かを保持します。
  * `component_name`（String; オプション）：ロード中のコンポーネントの名前を保持します。
  * `n_clicks`（Real; オプション）：この要素がクリックされた回数を表す整数です。
  * `n_clicks_timestamp`（Real; オプション）：n_clicks が変更された時刻（1970年からのミリ秒）を表す整数です。

これを使用して、どのボタンが最近変更されたかを判断できます。

  * `style`（Dict; オプション）：以前に設定されたスタイルを上書きする CSS スタイルを定義します。
  * `tag`（String; オプション）：listgroupitem に使用する HTML タグ、デフォルト：li
  * `target`（String; オプション）：リンクに渡すターゲット属性。外部リンクにのみ適用されます。
