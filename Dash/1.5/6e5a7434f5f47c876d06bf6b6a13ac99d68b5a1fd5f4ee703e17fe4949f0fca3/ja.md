```
dcc_radioitems(;kwargs...)
```

RadioItemsコンポーネントRadioItemsは、いくつかのラジオアイテム入力をカプセル化するコンポーネントです。RadioItemsの値とラベルは`options`プロパティで指定され、選択されたアイテムは`value`プロパティで指定されます。各ラジオアイテムは、周囲のラベルを持つ入力としてレンダリングされます。

  * `id` (String; optional): このコンポーネントのIDで、コールバック内でダッシュコンポーネントを識別するために使用されます。このIDは、アプリ内のすべてのコンポーネントで一意である必要があります。
  * `className` (String; optional): コンテナ（div）のクラス
  * `inline` (Bool; optional): オプションのラベルをインライン（true=水平）で表示するか、ブロック（false=垂直）で表示するかを示します。
  * `inputClassName` (String; optional): <input>ラジオ要素のクラス
  * `inputStyle` (Dict; optional): <input>ラジオ要素のスタイル
  * `labelClassName` (String; optional): ラジオ入力とオプションのラベルをラップする<label>のクラス
  * `labelStyle` (Dict; optional): ラジオ入力とオプションのラベルをラップする<label>のスタイル
  * `loading_state` (要素を含むリストはis*loading、prop*name、component*name - `is*loading`(Bool; optional): コンポーネントが読み込み中かどうかを判断します -`prop*name`(String; optional): どのプロパティが読み込み中かを保持します -`component*name` (String; optional): 読み込み中のコンポーネントの名前を保持します; optional): dash-rendererからの読み込み状態オブジェクトを保持するオブジェクト
  * `options` (optional): オプションの配列、またはオプションのインライン辞書。optionsは次の型を持ちます: String | Bool | Dict | 要素label、value、disabled、titleを含むリストの配列 - `label` (ダッシュコンポーネントのリストまたは単一、文字列または数値; required): オプションのラベル - `value` (String | Bool; required): オプションの値。この値は`value`プロパティで指定されたアイテムに対応します。 - `disabled` (Bool; optional): trueの場合、このオプションは無効で選択できません。 - `title` (String; optional): オプションのHTML 'title'属性。ホバー時の情報を提供します。この属性の詳細については、https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/titlesを参照してください。
  * `persisted_props` (Array of 'value's; optional): ユーザーの操作がコンポーネントまたはページを更新した後も持続するプロパティ。通常、このプロパティは無視できます。
  * `persistence` (Bool | String; optional): コンポーネントまたはページが更新されたときに、このコンポーネントでのユーザーの操作を持続させるために使用されます。`persisted`が真で、以前の値から変更されていない場合、アプリを使用している間にユーザーが変更した`value`は、その変更を保持します。新しい`value`が元々与えられたものと一致する限りです。`persistence_type`と併用して使用されます。
  * `persistence_type` ('local', 'session', 'memory'; optional): 持続されたユーザーの変更が保存される場所:

memory: メモリ内にのみ保持され、ページを更新するとリセットされます。 local: window.localStorage、ブラウザを終了してもデータが保持されます。 session: window.sessionStorage、ブラウザを終了するとデータがクリアされます。

  * `style` (Dict; optional): コンテナ（div）のスタイル
  * `value` (String | Bool; optional): 現在選択されている値
