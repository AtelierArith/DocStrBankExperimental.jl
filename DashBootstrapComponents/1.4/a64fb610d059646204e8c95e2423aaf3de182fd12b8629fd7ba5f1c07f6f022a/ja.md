```
dbc_carousel(;kwargs...)
```

カルーセルコンポーネント。Bootstrapカルーセルを作成するためのコンポーネント。このコンポーネントは、一連のコンテンツを循環させるスライドショーです。キーワード引数：

  * `id` (String; optional): コールバックでダッシュコンポーネントを識別するために使用されるコンポーネントのID。IDはアプリ内のすべてのコンポーネントで一意である必要があります。
  * `active_index` (Real; optional): 現在表示されているスライド番号
  * `className` (String; optional): **非推奨** 代わりに `class_name` を使用してください。

カルーセルコンテナのclassNameを定義します。一般的に、共通のプロパティを持つ要素をスタイルするためにCSSと一緒に使用されます。

  * `class_name` (String; optional): カルーセルコンテナのclassNameを定義します。一般的に、共通のプロパティを持つ要素をスタイルするためにCSSと一緒に使用されます。
  * `controls` (Bool; optional): 現在のスライドを変更するためのカルーセルの前後の矢印を表示します
  * `indicators` (Bool; optional): スライド位置インジケーターのセットを表示します
  * `interval` (Real; optional): カルーセルが自動的に循環する間隔 (デフォルト: 5000)

Noneに設定すると、カルーセルは自動再生しません（つまり、自動的に循環しません）。

  * `items` (required): カルーセルのスライドに表示するアイテム。itemsは次の型を持ちます: 'key', 'src', 'alt', 'img*class*name', 'imgClassName', 'img*style', 'header', 'caption', 'caption*class_name', 'captionClassName'を含むリストの配列。

これらの要素は次の型を持ちます：

  * `key` (String; optional): スライドの一意の識別子で、React.jsがコンポーネントをレンダリングする際のパフォーマンスを向上させるために使用されます

詳細については、https://reactjs.org/docs/lists-and-keys.htmlを参照してください。

  * `src` (String; optional): 画像のURL
  * `alt` (String; optional): 画像が表示できない場合の代替テキスト
  * `img_class_name` (String; optional): 画像のclassName。デフォルトは 'd-block w-100'
  * `imgClassName` (String; optional): **非推奨** 代わりに `img_class_name` を使用してください。

画像のclassName。デフォルトは 'd-block w-100'

  * `img_style` (Dict; optional): 画像のスタイル
  * `header` (String; optional): スライド上のテキストのヘッダー。<h5>要素に表示されます
  * `caption` (String; optional): アイテムのキャプション。テキストは<p>要素に表示されます
  * `caption_class_name` (String; optional): ヘッダーとキャプションコンテナのクラス名
  * `captionClassName` (String; optional): **非推奨** 代わりに `caption_class_name` を使用してください。

ヘッダーとキャプションコンテナのクラス名

  * `loading_state` (optional): dash-rendererからのローディング状態オブジェクトを保持するオブジェクト。loading*stateは次の型を持ちます: 'is*loading', 'prop*name', 'component*name'を含むリスト。

これらの要素は次の型を持ちます：

  * `is_loading` (Bool; optional): コンポーネントがロード中かどうかを判断します
  * `prop_name` (String; optional): どのプロパティがロード中かを保持します
  * `component_name` (String; optional): ロード中のコンポーネントの名前を保持します
  * `persisted_props` (Array of a value equal to: 'active_index's; optional): ユーザーの操作がコンポーネントまたはページをリフレッシュした後も持続するプロパティ。通常、このプロパティは無視できます。
  * `persistence` (Bool | String | Real; optional): コンポーネント - またはページ - がリフレッシュされたときに、このコンポーネントでのユーザーの操作を持続させるために使用されます。`persisted`が真で、以前の値から変更されていない場合、ユーザーがアプリを使用している間に変更した`value`はその変更を保持します。新しい`value`が元々与えられたものと一致する限り。
  * `persistence_type` (a value equal to: 'local', 'session', 'memory'; optional): 持続されたユーザーの変更が保存される場所：

memory: メモリ内にのみ保持され、ページリフレッシュ時にリセットされます。 local: window.localStorage、ブラウザを終了してもデータが保持されます。 session: window.sessionStorage、ブラウザを終了するとデータがクリアされます。

  * `ride` (a value equal to: 'carousel'; optional): ユーザーが最初のアイテムを手動で循環させた後、カルーセルを自動再生します。"carousel"の場合、ロード時にカルーセルを自動再生します。
  * `slide` (Bool; optional): カルーセルのスライドアニメーションが機能するかどうかを制御します
  * `style` (Dict; optional): カルーセルコンテナのCSSスタイルを定義します。以前に設定されたスタイルを上書きします。
  * `variant` (a value equal to: 'dark'; optional): より暗いコントロール、インジケーター、およびキャプションのためにカルーセルに `variant="dark"` を追加します。
