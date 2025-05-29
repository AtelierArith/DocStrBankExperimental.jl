```
dcc_checklist(;kwargs...)
```

チェックリストコンポーネント チェックリストは、いくつかのチェックボックスをカプセル化するコンポーネントです。チェックリストの値とラベルは `options` プロパティで指定され、チェックされた項目は `value` プロパティで指定されます。各チェックボックスは、周囲のラベルとともに入力としてレンダリングされます。

  * `id` (String; optional): このコンポーネントのIDで、コールバック内でダッシュコンポーネントを識別するために使用されます。このIDは、アプリ内のすべてのコンポーネントで一意である必要があります。
  * `className` (String; optional): コンテナ（div）のクラス
  * `inline` (Bool; optional): オプションのラベルをインライン（true=水平）で表示するか、ブロック（false=垂直）で表示するかを示します。
  * `inputClassName` (String; optional): <input> チェックボックス要素のクラス
  * `inputStyle` (Dict; optional): <input> チェックボックス要素のスタイル
  * `labelClassName` (String; optional): チェックボックス入力とオプションのラベルをラップする <label> のクラス
  * `labelStyle` (Dict; optional): チェックボックス入力とオプションのラベルをラップする <label> のスタイル
  * `loading_state` (要素を含むリスト is*loading, prop*name, component*name   - `is*loading`(Bool; optional): コンポーネントが読み込み中かどうかを判断します   -`prop*name`(String; optional): どのプロパティが読み込み中かを保持します   -`component*name` (String; optional): 読み込み中のコンポーネントの名前を保持します; optional): dash-renderer からの読み込み状態オブジェクトを保持するオブジェクト
  * `options` (optional): オプションの配列。options は次の型を持ちます: String | Bool | Dict の配列 | 要素 label, value, disabled, title を含むリストの配列   - `label` (ダッシュコンポーネント、文字列、または数値のリストまたは単一; required): オプションのラベル   - `value` (String | Bool; required): オプションの値。この値は `value` プロパティで指定された項目に対応します。   - `disabled` (Bool; optional): true の場合、このオプションは無効で選択できません。   - `title` (String; optional): オプションの HTML 'title' 属性。ホバー時の情報を提供します。この属性の詳細については、https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/titles を参照してください。
  * `persisted_props` (Array of 'value's; optional): ユーザーの操作がコンポーネントまたはページをリフレッシュした後も持続するプロパティ。通常、このプロパティは無視できます。
  * `persistence` (Bool | String; optional): コンポーネント - またはページ - がリフレッシュされたときに、このコンポーネントでのユーザーの操作を持続させるために使用されます。`persisted` が真であり、以前の値から変更されていない場合、アプリを使用している間にユーザーが変更した `value` は、その変更を保持します。ただし、新しい `value` が元々与えられたものと一致する必要があります。`persistence_type` と組み合わせて使用されます。
  * `persistence_type` ('local', 'session', 'memory'; optional): 持続されたユーザーの変更が保存される場所:

memory: メモリ内にのみ保持され、ページリフレッシュ時にリセットされます。 local: window.localStorage、データはブラウザを終了した後も保持されます。 session: window.sessionStorage、データはブラウザを終了するとクリアされます。

  * `style` (Dict; optional): コンテナ（div）のスタイル
  * `value` (Array of String | Bools; optional): 現在選択されている値
