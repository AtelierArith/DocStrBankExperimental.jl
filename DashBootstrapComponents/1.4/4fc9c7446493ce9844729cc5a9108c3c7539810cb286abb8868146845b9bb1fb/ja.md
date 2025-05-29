```
dbc_select(;kwargs...)
```

選択コンポーネント。BootstrapスタイルのHTML選択要素を作成します。オプションは、label、value、disabledのキーを持つ辞書のリストとして指定します。キーワード引数：

  * `id` (String; optional): このコンポーネントのIDで、コールバック内でダッシュコンポーネントを識別するために使用されます。このIDは、アプリ内のすべてのコンポーネントで一意である必要があります。
  * `className` (String; optional): **非推奨** `class_name`を代わりに使用してください。

CSSと共に使用され、共通のプロパティを持つ要素のスタイルを設定するために使用されます。

  * `class_name` (String; optional): CSSと共に使用され、共通のプロパティを持つ要素のスタイルを設定するために使用されます。
  * `disabled` (Bool; optional): Selectを無効にするにはTrueに設定します。
  * `html_size` (String; optional): これは、同時に表示されるべき選択肢の行数を表します。これにより、Selectはドロップダウンではなくスクロールリストボックスとしてレンダリングされます。
  * `invalid` (Bool; optional): フィードバック目的でInputに無効スタイルを適用します。これにより、valid=Falseの囲むdiv内のFormFeedbackが表示されます。
  * `key` (String; optional): コンポーネントの一意の識別子で、コンポーネントをレンダリングする際にReact.jsのパフォーマンスを向上させるために使用されます。詳細については、https://reactjs.org/docs/lists-and-keys.htmlを参照してください。
  * `name` (String; optional): フォームデータと共に送信されるコントロールの名前です。
  * `options` (optional): コンポーネント内にアイテムとして表示するオプションです。これは次のように配列または辞書であることができます：

1. ラベルと値が同じものであるオプションの配列 -

[string|number]

2. オプションの配列

```
{
  "label": [string|number],
  "value": [string|number],
  "disabled": [bool] (Optional),
  "title": [string] (Optional)
}
```

3. 辞書形式でのよりシンプルな`options`表現。順序は保証されません。すべての値とラベルは文字列として扱われます。

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

optionsは次の型を持ちます：Stringの配列 | 実数 | 辞書 | 'label'、'value'、'disabled'、'title'の要素を含むリストの配列。これらの要素は次の型を持ちます：

  * `label` (String | Real; required): オプションのラベル
  * `value` (String; required): オプションの値。この値は、`value`プロパティで指定されたアイテムに対応します。
  * `disabled` (Bool; optional): trueの場合、このチェックボックスは無効になり、クリックできません。
  * `title` (String; optional): オプションのHTML 'title'属性。ホバー時の情報を提供します。この属性の詳細については、https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/titlesを参照してください。
  * `persisted_props` (Array of a value equal to: 'value's; optional): ユーザーの操作がコンポーネントまたはページをリフレッシュした後も持続するプロパティ。通常、このプロパティは無視できます。
  * `persistence` (Bool | String | Real; optional): コンポーネントまたはページがリフレッシュされたときに、このコンポーネント内のユーザーの操作を持続させるために使用されます。`persisted`が真で、以前の値から変更されていない場合、ユーザーがアプリを使用中に変更した`value`は、その変更を保持します。新しい`value`が元々与えられたものと一致する限りです。`persistence_type`と共に使用されます。
  * `persistence_type` (a value equal to: 'local', 'session', 'memory'; optional): 持続されたユーザーの変更が保存される場所：

memory: メモリ内にのみ保持され、ページリフレッシュ時にリセットされます。local: window.localStorage、ブラウザを終了してもデータが保持されます。session: window.sessionStorage、ブラウザを終了するとデータがクリアされます。

  * `placeholder` (String; optional): 選択が行われる前に表示されるプレースホルダーテキスト。
  * `required` (a value equal to: 'required', 'REQUIRED' | Bool; optional): この属性は、ユーザーがフォームを送信する前に値を入力する必要があることを指定します。type属性がhidden、image、またはボタンタイプ（submit、reset、またはbutton）の場合には使用できません。:optionalおよび:requiredのCSS擬似クラスが適切にフィールドに適用されます。requiredはHTMLのブール属性であり、ブール値または'required'によって有効になります。代替の大文字表記`REQUIRED`も受け入れられます。
  * `size` (String; optional): Inputのサイズを設定します。オプション：'sm'（小）、'md'（中）、または'lg'（大）。デフォルトは'md'です。
  * `style` (Dict; optional): 以前に設定されたスタイルを上書きするCSSスタイルを定義します。
  * `valid` (Bool; optional): フィードバック目的でInputに有効スタイルを適用します。これにより、valid=Trueの囲むdiv内のFormFeedbackが表示されます。
  * `value` (String | Real; optional): 現在選択されているオプションの値です。
