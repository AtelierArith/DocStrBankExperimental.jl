```
dbc_breadcrumb(;kwargs...)
```

Breadcrumbコンポーネント。アプリ内でナビゲーションのパンくずリストを作成するためにパンくずリストを使用します。キーワード引数：

  * `id` (String; optional): このコンポーネントのIDで、コールバック内でダッシュコンポーネントを識別するために使用されます。

アプリ内のすべてのコンポーネントで一意である必要があります。

  * `className` (String; optional): **非推奨** - 代わりにclass_nameを使用してください。

一般的に、共通のプロパティを持つ要素のスタイルを設定するためにCSSと一緒に使用されます。

  * `class_name` (String; optional): 一般的に、共通のプロパティを持つ要素のスタイルを設定するためにCSSと一緒に使用されます。
  * `itemClassName` (String; optional): **非推奨** - 代わりにitem*class*nameを使用してください。

各アイテムに適用するクラス名。

  * `item_class_name` (String; optional): 各アイテムに適用するクラス名。
  * `item_style` (Dict; optional): パンくずリスト内の各アイテムに追加されるインラインCSSスタイルを定義します。
  * `items` (optional): このコンポーネント内にレンダリングするアイテムの詳細.. itemsは次の型を持ちます: 'label', 'href', 'active', 'external_link', 'target', 'title'を含むリストの配列。

これらの要素は次の型を持ちます：

  * `label` (String; optional): パンくずリスト内に表示するラベル。
  * `href` (String; optional): リンク先のリソースのURL
  * `active` (Bool; optional): このコンポーネントに「アクティブ」スタイルを適用します。
  * `external_link` (Bool; optional): trueの場合、ブラウザはこれを外部リンクとして扱い、新しい場所でページをリフレッシュします。falseの場合、これはページをリフレッシュすることなく場所を変更するだけです。たとえば、dcc.Locationを観察している場合に使用します。絶対URLの場合はtrue、そうでない場合はfalseがデフォルトです。
  * `target` (String; optional): リンクに渡すターゲット属性。外部リンクにのみ適用されます。
  * `title` (String; optional): 内部a要素のtitle属性
  * `key` (String; optional): コンポーネントの一意の識別子で、コンポーネントをレンダリングする際にReact.jsによるパフォーマンスを向上させるために使用されます。詳細についてはhttps://reactjs.org/docs/lists-and-keys.htmlを参照してください。
  * `loading_state` (optional): dash-rendererからのローディング状態オブジェクトを保持するオブジェクト。loading*stateは次の型を持ちます: 'is*loading', 'prop*name', 'component*name'を含むリスト。

これらの要素は次の型を持ちます：

  * `is_loading` (Bool; optional): コンポーネントが読み込まれているかどうかを判断します。
  * `prop_name` (String; optional): どのプロパティが読み込まれているかを保持します。
  * `component_name` (String; optional): 読み込まれているコンポーネントの名前を保持します。
  * `style` (Dict; optional): 以前に設定されたスタイルを上書きするCSSスタイルを定義します。
  * `tag` (Dict; optional): 外部パンくずリストコンポーネントに使用するHTMLタグ。デフォルト: "nav"。
