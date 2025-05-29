```
dcc_slider(;kwargs...)
```

スライダーコンポーネント 単一のハンドルを持つスライダーコンポーネント。

  * `id` (String; optional): このコンポーネントのIDで、コールバック内でダッシュコンポーネントを識別するために使用されます。

アプリ内のすべてのコンポーネントで一意である必要があります。

  * `className` (String; optional): ルートDOMノードの追加CSSクラス
  * `disabled` (Bool; optional): trueの場合、ハンドルを移動できません。
  * `dots` (Bool; optional): ステップ値が1より大きい場合、

スライダーをドットでレンダリングしたい場合は、ドットをtrueに設定できます。

  * `drag_value` (optional): ドラッグ中の入力の値
  * `included` (Bool; optional): 値がtrueの場合、連続した

値が含まれます。そうでない場合は、独立した値です。

  * `loading_state` (要素を含むリストは*loading、prop*name、component*name   - `is*loading`(Bool; optional): コンポーネントが読み込まれているかどうかを判断します   -`prop*name`(String; optional): どのプロパティが読み込まれているかを保持します   -`component*name` (String; optional): 読み込まれているコンポーネントの名前を保持します; optional): dash-rendererからの読み込み状態オブジェクトを保持するオブジェクト
  * `marks` (キーがStringで値がString | 要素を含むリストのDict label, style   - `label` (String; optional)   - `style` (Dict; optional); optional): スライダー上のマーク。

キーは位置（数値）を決定し、値は表示される内容を決定します。特定のマークポイントのスタイルを設定したい場合、値はスタイルとラベルプロパティを含むオブジェクトである必要があります。

  * `max` (optional): スライダーの最大許容値
  * `min` (optional): スライダーの最小許容値
  * `persisted_props` (Array of 'value's; optional): ユーザーの操作がコンポーネントまたはページを更新した後も持続するプロパティ。通常、このプロパティは無視できます。
  * `persistence` (Bool | String; optional): このコンポーネントでのユーザーの操作を持続させるために使用されます。

コンポーネントまたはページが更新されたときに。`persisted`が真であり、以前の値から変更されていない場合、ユーザーがアプリを使用している間に変更した`value`は、その変更を保持します。新しい`value`が元々与えられたものと一致する限り。`persistence_type`と組み合わせて使用されます。

  * `persistence_type` ('local', 'session', 'memory'; optional): 持続したユーザーの変更が保存される場所：

memory: メモリ内にのみ保持され、ページの更新時にリセットされます。 local: window.localStorage、ブラウザを終了した後もデータが保持されます。 session: window.sessionStorage、ブラウザを終了するとデータがクリアされます。

  * `step` (optional): 増分または減分が行われる値
  * `tooltip` (optional): 現在のスライダー値を説明するツールチップの設定。 tooltipは次のタイプを持ちます: 要素を含むリスト always*visible, placement   - `always*visible` (Bool; optional): ツールチップが常に表示されるべきかどうかを決定します

（デフォルトのホバー時に表示されるのとは対照的に）   - `placement` ('left', 'right', 'top', 'bottom', 'topLeft', 'topRight', 'bottomLeft', 'bottomRight'; optional): ツールチップの配置を決定します https://github.com/react-component/tooltip#api top/bottom{*}はツールチップの*起点*を設定します。例えば、`topLeft`は実際にはハンドルの右上に表示されます。

  * `updatemode` ('mouseup', 'drag'; optional): コンポーネントが`value`

プロパティを更新すべき時期を決定します。`mouseup`（デフォルト）の場合、スライダーはユーザーがスライダーのドラッグを終了したときのみその値をトリガーします。`drag`の場合、スライダーはドラッグ中に継続的にその値を更新します。ドラッグ中とドラッグ後に異なるアクションを希望する場合は、`updatemode`を`mouseup`のままにし、継続的に更新される値には`drag_value`を使用します。

  * `value` (optional): 入力の値
  * `vertical` (Bool; optional): trueの場合、スライダーは垂直になります
  * `verticalHeight` (optional): 垂直の場合のスライダーの高さ（px単位）。
