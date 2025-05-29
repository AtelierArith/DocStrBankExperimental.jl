```
dcc_clipboard(;kwargs...)
```

クリップボードコンポーネント クリップボードコンポーネントはテキストをクリップボードにコピーします

  * `id` (String; optional): このコンポーネントを識別するために使用されるID。
  * `className` (String; optional): アイコン要素のクラス名
  * `content` (String; optional): `target_id`がNoneの場合にクリップボードにコピーされるテキスト。
  * `loading_state` (要素を含むリスト is*loading, prop*name, component*name   - `is*loading`(Bool; optional): コンポーネントが読み込み中かどうかを決定します   -`prop*name`(String; optional): どのプロパティが読み込み中かを保持します   -`component*name` (String; optional): 読み込み中のコンポーネントの名前を保持します; optional): dash-rendererからの読み込み状態オブジェクトを保持するオブジェクト
  * `n_clicks` (optional): コピーボタンがクリックされた回数
  * `style` (Dict; optional): アイコンのスタイル
  * `target_id` (String | Dict; optional): クリップボードにコピーするテキストを含むターゲットコンポーネントのID。

`children`プロパティの内部テキストがクリップボードにコピーされます。 もしなければ、`value`プロパティのテキストがコピーされます。

  * `title` (String; optional): コピーアイコンにマウスをホバーしたときにツールチップとして表示されるテキスト。
