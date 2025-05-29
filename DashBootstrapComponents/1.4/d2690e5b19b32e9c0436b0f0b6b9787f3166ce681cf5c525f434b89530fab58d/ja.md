```
dbc_radiobutton(;kwargs...)
```

ラジオボタンコンポーネント。チェックリストは、いくつかのチェックボックスをカプセル化するコンポーネントです。チェックリストの値とラベルは`options`プロパティで指定され、チェックされた項目は`value`プロパティで指定されます。各チェックボックスは入力/ラベルペアとしてレンダリングされます。`Checklist`は正しく機能するために`id`を与えられる必要があります。キーワード引数：

  * `id` (String; optional): このコンポーネントのIDで、コールバック内でダッシュコンポーネントを識別するために使用されます。

IDはアプリ内のすべてのコンポーネントで一意である必要があります。

  * `className` (String; optional): **非推奨** `class_name`を代わりに使用してください。

コンテナ（div）のクラス

  * `class_name` (String; optional): コンテナ（div）のクラス
  * `disabled` (Bool; optional): ラジオボタンを無効にします。
  * `inputClassName` (String; optional): **非推奨** `input_class_name`を代わりに使用してください。

<input>チェックボックス要素のクラス

  * `inputStyle` (Dict; optional): **非推奨** `input_style`を代わりに使用してください。

<input>チェックボックス要素のスタイル。

  * `input_class_name` (String; optional): <input>チェックボックス要素のクラス
  * `input_style` (Dict; optional): <input>チェックボックス要素のスタイル。
  * `label` (リストまたは単一のダッシュコンポーネント、文字列または数値; optional): <input>要素のラベル
  * `labelClassName` (String; optional): **非推奨** `label_class_name`を代わりに使用してください。

各項目の<label>要素に適用するCSSクラス。

  * `labelStyle` (Dict; optional): **非推奨** `label_style`を代わりに使用してください。

各項目の<label>要素に適用するインラインスタイル引数。

  * `label_class_name` (String; optional): 各項目の<label>要素に適用するCSSクラス。
  * `label_id` (String; optional): ラベルのID
  * `label_style` (Dict; optional): 各項目の<label>要素に適用するインラインスタイル引数。
  * `loading_state` (optional): dash-rendererからのローディング状態オブジェクトを保持するオブジェクト。loading*stateは次の型を持ちます: 'is*loading', 'prop*name', 'component*name'を含むリスト。

これらの要素は次の型を持ちます：

  * `is_loading` (Bool; optional): コンポーネントがロード中かどうかを決定します。
  * `prop_name` (String; optional): どのプロパティがロード中かを保持します。
  * `component_name` (String; optional): ロード中のコンポーネントの名前を保持します。
  * `name` (String; optional): フォームデータと共に送信されるコントロールの名前。
  * `persisted_props` (値が'value'と等しい配列; optional): ユーザーの操作がコンポーネントまたはページをリフレッシュした後も持続するプロパティ。通常、このプロパティは無視できます。
  * `persistence` (Bool | String | Real; optional): コンポーネント - またはページ - がリフレッシュされたときに、このコンポーネントでのユーザーの操作を持続させるために使用されます。`persisted`が真で、以前の値から変更されていない場合、アプリを使用中にユーザーが変更した`value`はその変更を保持します。新しい`value`が元々与えられたものと一致する限り。
  * `persistence_type` (値が: 'local', 'session', 'memory'と等しい; optional): 持続されたユーザーの変更が保存される場所：

memory: メモリ内にのみ保持され、ページリフレッシュ時にリセットされます。local: window.localStorage、ブラウザを終了した後もデータが保持されます。session: window.sessionStorage、ブラウザを終了するとデータがクリアされます。

  * `style` (Dict; optional): コンテナ（div）のスタイル
  * `value` (Bool; optional): 入力の値。
