```
dbc_dropdownmenu(;kwargs...)
dbc_dropdownmenu(children::Any;kwargs...)
dbc_dropdownmenu(children_maker::Function;kwargs...)
```

DropdownMenuコンポーネント。DropdownMenuは、ナビゲーションやその他のインタラクティブな要素を整理するためにリンクやその他のコンテンツをグループ化するのに便利なオーバーレイを作成します。キーワード引数：

  * `children`（リストまたは単一のダッシュコンポーネント、文字列または数値; オプション）：このコンポーネントの子要素。
  * `id`（文字列; オプション）：コールバック内でダッシュコンポーネントを識別するために使用されるこのコンポーネントのID。IDはアプリ内のすべてのコンポーネントで一意である必要があります。
  * `addon_type`（Bool | 'prepend'、'append'と等しい値; オプション）：DropdownMenuが入力グループ内で使用されている場合は、これを'prepend'または'append'に設定します。
  * `align_end`（Bool; オプション）：親の右側にDropdownMenuを揃えます。デフォルト：False。
  * `caret`（Bool; オプション）：DropdownMenuトグルにキャレットを追加します。デフォルト：True。
  * `className`（文字列; オプション）：**非推奨** `class_name`を代わりに使用してください。

一般的に、共通のプロパティを持つ要素のスタイルを設定するためにCSSと一緒に使用されます。

  * `class_name`（文字列; オプション）：一般的に、共通のプロパティを持つ要素のスタイルを設定するためにCSSと一緒に使用されます。
  * `color`（文字列; オプション）：DropdownMenuトグルの色を設定します。利用可能なオプションは：'primary'、

'secondary'、'success'、'warning'、'danger'、'info'、'link'または任意の有効なCSSカラー（例：16進数コード、10進数コード、またはCSSカラー名）です。デフォルト：'primary'

  * `direction`（'down'、'start'、'end'、'up'、'left'、'right'、'end'と等しい値; オプション）：DropdownMenuを展開する方向。デフォルト：'down'。`left`

および`right`は非推奨であり、代わりに`start`および`end`を使用する必要があります。

  * `disabled`（Bool; オプション）：ドロップダウンを無効にします。
  * `group`（Bool; オプション）：DropdownMenuがButtonGroup内にある場合は、グループをTrueに設定します。
  * `in_navbar`（Bool; オプション）：DropdownMenuがナビゲーションバー内にある場合は、これをTrueに設定します。デフォルト：False。
  * `key`（文字列; オプション）：コンポーネントの一意の識別子で、コンポーネントをレンダリングする際にReact.jsによってパフォーマンスを向上させるために使用されます。詳細については、https://reactjs.org/docs/lists-and-keys.htmlを参照してください。
  * `label`（リストまたは単一のダッシュコンポーネント、文字列または数値; オプション）：DropdownMenuトグルのラベル。
  * `loading_state`（オプション）：dash-rendererからのローディング状態オブジェクトを保持するオブジェクト。loading*stateは次の型を持ちます：要素'is*loading'、'prop*name'、'component*name'を含むリスト。

これらの要素は次の型を持ちます：

  * `is_loading`（Bool; オプション）：コンポーネントがローディング中かどうかを判断します。
  * `prop_name`（文字列; オプション）：どのプロパティがローディング中かを保持します。
  * `component_name`（文字列; オプション）：ローディング中のコンポーネントの名前を保持します。
  * `menu_variant`（'light'、'dark'と等しい値; オプション）：ダークモードのドロップダウンを作成するには`menu_variant="dark"`を設定します。
  * `nav`（Bool; オプション）：DropdownMenuが他のナビアイテムと一貫したスタイルのナビ内にある場合は、これをTrueに設定します。デフォルト：False。
  * `right`（Bool; オプション）：**非推奨** `align_end`を代わりに使用してください。

親の右側にDropdownMenuを揃えます。デフォルト：False。

  * `size`（'sm'、'md'、'lg'と等しい値; オプション）：DropdownMenuのサイズ。'sm'は小、'md'は中、'lg'は大に対応します。
  * `style`（辞書; オプション）：以前に設定されたスタイルを上書きするCSSスタイルを定義します。
  * `toggleClassName`（文字列; オプション）：**非推奨** `toggle_class_name`を代わりに使用してください。

一般的に、共通のプロパティを持つ要素のスタイルを設定するためにCSSと一緒に使用されます。このプロパティで指定されたクラスは、DropdownMenuトグルに適用されます。

  * `toggle_class_name`（文字列; オプション）：一般的に、共通のプロパティを持つ要素のスタイルを設定するためにCSSと一緒に使用されます。このプロパティで指定されたクラスは、DropdownMenuトグルに適用されます。
  * `toggle_style`（辞書; オプション）：以前に設定されたスタイルを上書きするCSSスタイルを定義します。ここで設定されたスタイルは、DropdownMenuトグルに適用されます。
