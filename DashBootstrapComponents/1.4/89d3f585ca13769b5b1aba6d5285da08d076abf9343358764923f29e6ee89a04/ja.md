```
dbc_inputgrouptext(;kwargs...)
dbc_inputgrouptext(children::Any;kwargs...)
dbc_inputgrouptext(children_maker::Function;kwargs...)
```

InputGroupText コンポーネント。InputGroups 内のテキストをラップするために使用します。キーワード引数:

  * `children` (ダッシュコンポーネント、文字列、または数値のリストまたは単一; オプション): このコンポーネントの子要素。
  * `id` (String; オプション): このコンポーネントの ID で、コールバック内でダッシュコンポーネントを識別するために使用されます。ID はアプリ内のすべてのコンポーネントで一意である必要があります。
  * `className` (String; オプション): **非推奨** `class_name` を代わりに使用してください。

一般的に、共通のプロパティを持つ要素のスタイルを設定するために CSS と一緒に使用されます。

  * `class_name` (String; オプション): 一般的に、共通のプロパティを持つ要素のスタイルを設定するために CSS と一緒に使用されます。
  * `key` (String; オプション): コンポーネントの一意の識別子で、コンポーネントをレンダリングする際に React.js によってパフォーマンスを向上させるために使用されます。詳細については https://reactjs.org/docs/lists-and-keys.html を参照してください。
  * `loading_state` (オプション): dash-renderer からのローディング状態オブジェクトを保持するオブジェクト。loading*state は次の型を持ちます: 'is*loading', 'prop*name', 'component*name' を含むリスト。

これらの要素は次の型を持ちます:

  * `is_loading` (Bool; オプション): コンポーネントがロード中かどうかを判断します。
  * `prop_name` (String; オプション): どのプロパティがロード中かを保持します。
  * `component_name` (String; オプション): ロード中のコンポーネントの名前を保持します。
  * `style` (Dict; オプション): 以前に設定されたスタイルを上書きする CSS スタイルを定義します。
