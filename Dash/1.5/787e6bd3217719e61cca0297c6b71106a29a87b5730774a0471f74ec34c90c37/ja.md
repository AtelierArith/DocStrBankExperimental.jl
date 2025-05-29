```
dcc_dropdown(;kwargs...)
```

ドロップダウンコンポーネント Dropdown は、1つまたは複数のアイテムを選択するためのインタラクティブなドロップダウン要素です。ドロップダウンアイテムの値とラベルは `options` プロパティで指定され、選択されたアイテムは `value` プロパティで指定されます。

オプションが多い場合（5つ以上）や、スペースに制約がある場合はドロップダウンを使用します。それ以外の場合は、すべてのアイテムを一度に表示できる RadioItems や Checklist を使用できます。

  * `id` (String; optional): このコンポーネントの ID で、コールバック内でダッシュコンポーネントを識別するために使用されます。この ID は、アプリ内のすべてのコンポーネントで一意である必要があります。
  * `className` (String; optional): ドロップダウン要素の className
  * `clearable` (Bool; optional): ドロップダウンが「クリア可能」であるかどうか、つまり、選択された値を削除する小さな「x」がドロップダウンの右側に表示されるかどうか。
  * `disabled` (Bool; optional): true の場合、このドロップダウンは無効になり、選択を変更できません。
  * `loading_state` (要素を含むリスト is*loading, prop*name, component*name   - `is*loading`(Bool; optional): コンポーネントが読み込み中かどうかを判断します   -`prop*name`(String; optional): どのプロパティが読み込み中かを保持します   -`component*name` (String; optional): 読み込み中のコンポーネントの名前を保持します; optional): dash-renderer からの読み込み状態オブジェクトを保持するオブジェクト
  * `maxHeight` (optional): オプションドロップダウンの高さ。
  * `multi` (Bool; optional): true の場合、ユーザーは複数の値を選択できます
  * `optionHeight` (optional): 各オプションの高さ。ラベルの長さが折り返される場合に増加させることができます
  * `options` (optional): オプションの配列 {label: [string|number], value: [string|number]}、各オプションに対してオプションの disabled フィールドを使用できます。options の型は次の通りです: String | Bools | Dict | 要素 label, value, disabled, title, search を含むリストの配列   - `label` (ダッシュコンポーネントのリストまたは単一、文字列または数値; 必須): オプションのラベル   - `value` (String | Bool; 必須): オプションの値。この値は `value` プロパティで指定されたアイテムに対応します。   - `disabled` (Bool; optional): true の場合、このオプションは無効で選択できません。   - `title` (String; optional): オプションの HTML 'title' 属性。ホバー時の情報を提供します。この属性の詳細については、https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/title を参照してください。   - `search` (String; optional): オプションのオプションの検索値。ラベルがコンポーネントである場合や、ラベルとは異なるカスタム検索値を提供する場合に使用します。検索値がなく、ラベルがコンポーネントの場合、`value` が検索に使用されます。
  * `persisted_props` (Array of 'value's; optional): ユーザーの操作がコンポーネントまたはページをリフレッシュした後も持続するプロパティ。通常、このプロパティは無視できます。

  * `persistence` (Bool | String; optional): コンポーネントまたはページがリフレッシュされたときに、このコンポーネントでのユーザーの操作を持続させるために使用されます。`persisted` が真で、以前の値から変更されていない場合、アプリを使用している間にユーザーが変更した `value` はその変更を保持します。ただし、新しい `value` が元々与えられたものと一致する必要があります。`persistence_type` と組み合わせて使用されます。
  * `persistence_type` ('local', 'session', 'memory'; optional): 持続されたユーザーの変更が保存される場所:

memory: メモリ内にのみ保持され、ページをリフレッシュするとリセットされます。 local: window.localStorage、ブラウザを終了してもデータが保持されます。 session: window.sessionStorage、ブラウザを終了するとデータがクリアされます。

  * `placeholder` (String; optional): オプションが選択されていないときに表示される灰色のデフォルトテキスト
  * `search_value` (String; optional): 検索のためにドロップダウンに入力された値。
  * `searchable` (Bool; optional): 検索機能を有効にするかどうか
  * `style` (Dict; optional): 以前に設定されたスタイルを上書きする CSS スタイルを定義します。
  * `value` (String | Bool | Array of String | Bools; optional): 入力の値。`multi` が false (デフォルト) の場合、値は `options` プロパティで提供された値に対応する文字列です。`multi` が true の場合、複数の値を一度に選択でき、`value` は `options` プロパティの値に対応するアイテムの配列です。

```
