```
dbc_card(;kwargs...)
dbc_card(children::Any;kwargs...)
dbc_card(children_maker::Function;kwargs...)
```

カードコンポーネント。Bootstrapカードを作成するためのコンポーネント。CardBody、CardImg、CardLink、CardHeader、CardFooterと組み合わせて使用します。また、CardColumns、CardDeck、CardGroupと組み合わせて異なるレイアウトオプションを使用することもできます。キーワード引数：

  * `children`（リストまたは単一のダッシュコンポーネント、文字列または数値; オプション）：このコンポーネントの子要素
  * `id`（文字列; オプション）：このコンポーネントのIDで、ダッシュコンポーネントを識別するために使用されます。

コールバック内で。IDはアプリ内のすべてのコンポーネントで一意である必要があります。

  * `body`（Bool; オプション）：カードに`card-body`クラスを適用し、このカードの子要素にCardBodyコンポーネントを含める必要がなくなります。デフォルト：False
  * `className`（文字列; オプション）：**非推奨** `class_name`を代わりに使用してください。

一般的に、共通のプロパティを持つ要素のスタイルを設定するためにCSSと一緒に使用されます。

  * `class_name`（文字列; オプション）：一般的に、共通のプロパティを持つ要素のスタイルを設定するためにCSSと一緒に使用されます。
  * `color`（文字列; オプション）：カードの色、オプション：primary、secondary、success、info、warning、danger、

light、darkまたはお好みの有効なCSS色（例：16進数コード、10進数コード、またはCSS色名）。デフォルトはlightです。

  * `inverse`（Bool; オプション）：暗い背景で使用するためにテキストの色を反転させます。
  * `key`（文字列; オプション）：コンポーネントの一意の識別子で、コンポーネントをレンダリングする際にReact.jsのパフォーマンスを向上させるために使用されます。詳細についてはhttps://reactjs.org/docs/lists-and-keys.htmlを参照してください。
  * `loading_state`（オプション）：dash-rendererからのローディング状態オブジェクトを保持するオブジェクト。loading*stateは次のタイプを持ちます：要素'is*loading'、'prop*name'、'component*name'を含むリスト。

これらの要素は次のタイプを持ちます：

  * `is_loading`（Bool; オプション）：コンポーネントがロード中かどうかを判断します。
  * `prop_name`（文字列; オプション）：どのプロパティがロード中かを保持します。
  * `component_name`（文字列; オプション）：ロード中のコンポーネントの名前を保持します。
  * `outline`（Bool; オプション）：カードの境界線にのみ色のスタイリングを適用します。
  * `style`（辞書; オプション）：以前に設定されたスタイルを上書きするCSSスタイルを定義します。
