```
dbc_checklist(;kwargs...)
```

チェックリストコンポーネント。チェックリストは、いくつかのチェックボックスをカプセル化するコンポーネントです。チェックリストの値とラベルは`options`プロパティで指定され、チェックされた項目は`value`プロパティで指定されます。各チェックボックスは入力/ラベルペアとしてレンダリングされます。`Checklist`は正しく動作するために`id`を与えられる必要があります。キーワード引数：

  * `id` (String; optional): このコンポーネントのIDで、コールバック内でダッシュコンポーネントを識別するために使用されます。

IDはアプリ内のすべてのコンポーネントで一意である必要があります。

  * `className` (String; optional): **非推奨** `class_name`を代わりに使用してください。

コンテナ（div）のクラス

  * `class_name` (String; optional): コンテナ（div）のクラス
  * `inline` (Bool; optional): チェックリストをインラインで配置
  * `inputCheckedClassName` (String; optional): **非推奨** `input_checked_class_name`を代わりに使用してください。

対応するチェックボックスがチェックされているときに<input>要素に適用する追加のCSSクラス。

  * `inputCheckedStyle` (Dict; optional): **非推奨** `input_checked_style`を代わりに使用してください。

チェックされた項目の<input>要素に適用する追加のインラインスタイル引数。

  * `inputClassName` (String; optional): **非推奨** `input_class_name`を代わりに使用してください。

<input>チェックボックス要素のクラス

  * `inputStyle` (Dict; optional): **非推奨** `input_style`を代わりに使用してください。

<input>チェックボックス要素のスタイル。

  * `input_checked_class_name` (String; optional): 対応するチェックボックスがチェックされているときに<input>要素に適用する追加のCSSクラス。
  * `input_checked_style` (Dict; optional): チェックされた項目の<input>要素に適用する追加のインラインスタイル引数。
  * `input_class_name` (String; optional): <input>チェックボックス要素のクラス
  * `input_style` (Dict; optional): <input>チェックボックス要素のスタイル。
  * `key` (String; optional): コンポーネントの一意の識別子で、コンポーネントをレンダリングする際にReact.jsによってパフォーマンスを向上させるために使用されます。詳細についてはhttps://reactjs.org/docs/lists-and-keys.htmlを参照してください。
  * `labelCheckedClassName` (String; optional): **非推奨** `label_checked_class_name`を代わりに使用してください。

対応するチェックボックスがチェックされているときに<label>要素に適用する追加のCSSクラス。

  * `labelCheckedStyle` (Dict; optional): **非推奨** `label_checked_style`を代わりに使用してください。

チェックされた項目の<label>要素に適用する追加のインラインスタイル引数。

  * `labelClassName` (String; optional): **非推奨** `label_class_name`を代わりに使用してください。

各項目の<label>要素に適用するCSSクラス。

  * `labelStyle` (Dict; optional): **非推奨** `label_style`を代わりに使用してください。

各項目の<label>要素に適用するインラインスタイル引数。

  * `label_checked_class_name` (String; optional): 対応するチェックボックスがチェックされているときに<label>要素に適用する追加のCSSクラス。
  * `label_checked_style` (Dict; optional): チェックされた項目の<label>要素に適用する追加のインラインスタイル引数。
  * `label_class_name` (String; optional): 各項目の<label>要素に適用するCSSクラス。
  * `label_style` (Dict; optional): 各項目の<label>要素に適用するインラインスタイル引数。
  * `loading_state` (optional): dash-rendererからのローディング状態オブジェクトを保持するオブジェクト。loading*stateは次の型を持ちます：要素'is*loading'、'prop*name'、'component*name'を含むリスト。

これらの要素は次の型を持ちます：

  * `is_loading` (Bool; optional): コンポーネントがロード中かどうかを判断します。
  * `prop_name` (String; optional): どのプロパティがロード中かを保持します。
  * `component_name` (String; optional): ロード中のコンポーネントの名前を保持します。
  * `name` (String; optional): フォームデータと共に送信されるコントロールの名前。
  * `options` (optional): コンポーネント内にアイテムとして表示するオプション。これは次のように配列または辞書であることができます：

1. ラベルと値が同じであるオプションの配列 -

[string|number]

2. オプションの配列

```
{
  "label": [string|number],
  "value": [string|number],
  "disabled": [bool] (Optional),
  "input_id": [string] (Optional),
  "label_id": [string] (Optional)
}
```

3. 辞書形式でのより簡単な`options`表現。順序は保証されません。すべての値とラベルは文字列として扱われます。

```
{"value1": "label1", "value2": "label2", ... }
```

これは次のものと等しいです。

```
[
  {"label": "label1", "value": "value1"},
  {"label": "label2", "value": "value2"}, ...
]
```

optionsは次の型を持ちます：Stringの配列 | 実数 | 辞書 | 要素'label'、'value'、'disabled'、'input*id'、'label*id'を含むリストの配列。これらの要素は次の型を持ちます：

  * `label` (ダッシュコンポーネントのリストまたは単一、文字列または数値; 必須): チェックボックスのラベル
  * `value` (String | Real; 必須): チェックボックスの値。この値は`value`プロパティで指定された項目に対応します。
  * `disabled` (Bool; optional): trueの場合、このチェックボックスは無効でクリックできません。
  * `input_id` (String; optional): このオプションの入力のIDで、ツールチップを添付したりCSSスタイルを適用するために使用できます。
  * `label_id` (String; optional): このオプションのラベルのIDで、ツールチップを添付したりCSSスタイルを適用するために使用できます。
  * `persisted_props` (値が'value'sに等しい配列; optional): ユーザーの操作がコンポーネントまたはページをリフレッシュした後も持続するプロパティ。通常、このプロパティは無視できます。
  * `persistence` (Bool | String | Real; optional): このコンポーネント内のユーザーの操作がコンポーネントまたはページがリフレッシュされたときに持続することを許可するために使用されます。`persisted`が真であり、以前の値から変更されていない場合、アプリを使用している間にユーザーが変更した`value`は、その変更を保持します。新しい`value`が元々与えられたものと一致する限り。
  * `persistence_type` (値が'local'、'session'、'memory'に等しい; optional): 持続されたユーザーの変更が保存される場所：

memory: メモリ内にのみ保持され、ページリフレッシュ時にリセットされます。local: window.localStorage、ブラウザを終了した後もデータが保持されます。session: window.sessionStorage、ブラウザを終了するとデータがクリアされます。

  * `style` (Dict; optional): コンテナ（div）のスタイル
  * `switch` (Bool; optional): チェックボックスの代わりにトグルのようなスイッチをレンダリングするにはTrueに設定します。
  * `value` (Array of String | Reals; optional): 現在選択されている値

```
