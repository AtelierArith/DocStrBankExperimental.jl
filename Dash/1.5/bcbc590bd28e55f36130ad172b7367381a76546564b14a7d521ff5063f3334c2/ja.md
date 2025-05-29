```
dcc_rangeslider(;kwargs...)
```

RangeSliderコンポーネント 二つのハンドルを持つダブルスライダー。数値の範囲を指定するために使用されます。

  * `id` (String; optional): このコンポーネントのIDで、コールバック内でダッシュコンポーネントを識別するために使用されます。IDはアプリ内のすべてのコンポーネントで一意である必要があります。
  * `allowCross` (Bool; optional): allowCrossをtrueに設定すると、ハンドルが交差することを許可します。
  * `className` (String; optional): ルートDOMノードの追加CSSクラス
  * `count` (optional): レンダリングする範囲の数を決定し、複数のハンドルがレンダリングされます（数 + 1）。
  * `disabled` (Bool; optional): trueの場合、ハンドルを移動できません。
  * `dots` (Bool; optional): ステップ値が1より大きい場合、スライダーをドットでレンダリングしたい場合は、dotsをtrueに設定できます。
  * `drag_value` (Array of s; optional): ドラッグ中の入力の値
  * `included` (Bool; optional): 値がtrueの場合、連続した値が含まれます。そうでない場合は、独立した値です。
  * `loading_state` (要素を含むリスト is*loading, prop*name, component*name   - `is*loading`(Bool; optional): コンポーネントが読み込み中かどうかを判断します   -`prop*name`(String; optional): どのプロパティが読み込み中かを保持します   -`component*name` (String; optional): 読み込み中のコンポーネントの名前を保持します; optional): dash-rendererからの読み込み状態オブジェクトを保持するオブジェクト
  * `marks` (キーがStringで値がString | 要素を含むリスト label, styleのDict   - `label` (String; optional)   - `style` (Dict; optional); optional): スライダー上のマーク。

キーは位置（数値）を決定し、値は表示される内容を決定します。特定のマークポイントのスタイルを設定したい場合、値はstyleとlabelプロパティを含むオブジェクトである必要があります。

  * `max` (optional): スライダーの最大許容値
  * `min` (optional): スライダーの最小許容値
  * `persisted_props` (Array of 'value's; optional): ユーザーの操作がコンポーネントまたはページをリフレッシュした後も持続するプロパティ。通常、このプロパティは無視できます。
  * `persistence` (Bool | String; optional): コンポーネントまたはページがリフレッシュされたときに、このコンポーネントのユーザー操作を持続させるために使用されます。`persisted`が真で、以前の値から変更されていない場合、ユーザーがアプリを使用中に変更した`value`は、その変更を保持します。新しい`value`が元々与えられたものと一致する限り。`persistence_type`と併用して使用されます。
  * `persistence_type` ('local', 'session', 'memory'; optional): 持続されたユーザーの変更が保存される場所：

memory: メモリ内にのみ保持され、ページリフレッシュ時にリセットされます。 local: window.localStorage、ブラウザを終了した後もデータが保持されます。 session: window.sessionStorage、ブラウザを終了するとデータがクリアされます。

  * `pushable` (Bool; optional): pushableをtrueに設定すると、ハンドルを移動する際に周囲のハンドルを押すことができます。数値に設定すると、その数値がハンドル間の最小確保距離になります。
  * `step` (optional): 増分または減分が行われる値
  * `tooltip` (optional): 現在のスライダー値を説明するツールチップの設定。tooltipは次のタイプを持ちます: 要素を含むリスト always*visible, placement   - `always*visible`(Bool; optional): ツールチップが常に表示されるべきかどうかを判断します（デフォルトは、ホバー時に表示される）   -`placement`('left', 'right', 'top', 'bottom', 'topLeft', 'topRight', 'bottomLeft', 'bottomRight'; optional): ツールチップの配置を決定します https://github.com/react-component/tooltip#api top/bottom{*}はツールチップの*起点*を設定します。例えば、`topLeft`は実際にはハンドルの右上に表示されます。
  * `updatemode` ('mouseup', 'drag'; optional): コンポーネントが`value`プロパティを更新すべき時期を決定します。`mouseup`（デフォルト）の場合、スライダーはユーザーがスライダーのドラッグを終了したときのみその値をトリガーします。`drag`の場合、スライダーはドラッグ中に継続的にその値を更新します。後者の場合、`drag_value`プロパティを代わりに使用できます。
  * `value` (Array of s; optional): 入力の値
  * `vertical` (Bool; optional): trueの場合、スライダーは垂直になります。
  * `verticalHeight` (optional): 垂直の場合のスライダーの高さ（px単位）。
