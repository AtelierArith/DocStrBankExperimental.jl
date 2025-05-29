```
dbc_pagination(;kwargs...)
```

ページネーションコンポーネント。ページネーションUIを構築するためのプレゼンテーショナルコンポーネントのコンテナ。個々のページは`PaginationItem`コンポーネントを使用して子として追加する必要があります。キーワード引数：

  * `id` (String; optional): このコンポーネントのIDで、コールバック内でダッシュコンポーネントを識別するために使用されます。このIDはアプリ内のすべてのコンポーネントで一意である必要があります。
  * `active_page` (Real; optional): 現在アクティブなページ
  * `className` (String; optional): **非推奨** - 代わりにclass_nameを使用してください。

一般的に、共通のプロパティを持つ要素のスタイルを設定するためにCSSと一緒に使用されます。

  * `class_name` (String; optional): 一般的に、共通のプロパティを持つ要素のスタイルを設定するためにCSSと一緒に使用されます。
  * `first_last` (Bool; optional): Trueの場合、コンポーネントの最初と最後にアイコンを表示します。
  * `fully_expanded` (Bool; optional): Trueの場合、`min_value`と`max_value`の間のすべての数字を表示します。
  * `loading_state` (optional): dash-rendererからのローディング状態オブジェクトを保持するオブジェクト。loading*stateは次のタイプを持ちます：要素'is*loading'、'prop*name'、'component*name'を含むリスト。

これらの要素は次のタイプを持ちます：

  * `is_loading` (Bool; optional): コンポーネントがローディング中かどうかを判断します
  * `prop_name` (String; optional): どのプロパティがローディング中かを保持します
  * `component_name` (String; optional): ローディング中のコンポーネントの名前を保持します
  * `max_value` (Real; required): ページネーションに表示される最大（最右）値。定義する必要があります。

`min_value`と`step`が一緒にこの値に達することができない場合、次のステップ値が最大値として使用されます。

  * `min_value` (Real; optional): ページネーションに表示される最小（最左）値。
  * `previous_next` (Bool; optional): Trueの場合、個々のページ番号の前後に前と次のアイコンを表示します。
  * `size` (値は: 'sm', 'lg'と等しい; optional): ページネーション内のすべてのページアイテムのサイズを設定します。
  * `step` (Real; optional): ページの増分ステップ。
  * `style` (Dict; optional): 以前に設定されたスタイルを上書きするCSSスタイルを定義します。
