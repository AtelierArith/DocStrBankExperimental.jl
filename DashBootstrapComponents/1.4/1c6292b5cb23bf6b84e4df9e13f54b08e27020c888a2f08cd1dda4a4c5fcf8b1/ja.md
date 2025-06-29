```
dbc_dropdownmenuitem(;kwargs...)
dbc_dropdownmenuitem(children::Any;kwargs...)
dbc_dropdownmenuitem(children_maker::Function;kwargs...)
```

DropdownMenuItem コンポーネント。DropdownMenu のコンテンツを構築するために DropdownMenuItem を使用します。キーワード引数：

  * `children`（ダッシュコンポーネント、文字列、または数値のリストまたは単一; オプション）：このコンポーネントの子要素。
  * `id`（文字列; オプション）：コールバックでダッシュコンポーネントを識別するために使用されるこのコンポーネントの ID。ID はアプリ内のすべてのコンポーネントで一意である必要があります。
  * `active`（ブール; オプション）：このアイテムを「アクティブ」としてスタイル設定します。
  * `className`（文字列; オプション）：**非推奨** `class_name` を代わりに使用してください。

一般的に、共通のプロパティを持つ要素をスタイル設定するために CSS と一緒に使用されます。

  * `class_name`（文字列; オプション）：一般的に、共通のプロパティを持つ要素をスタイル設定するために CSS と一緒に使用されます。
  * `disabled`（ブール; オプション）：このアイテムを「無効」としてスタイル設定します。
  * `divider`（ブール; オプション）：このエントリが区切りである場合は True に設定します。通常、子要素はありません。
  * `external_link`（ブール; オプション）：true の場合、ブラウザはこれを外部リンクとして扱い、

新しい場所でページをリフレッシュします。false の場合、これはページのリフレッシュをトリガーせずに単に場所を変更します。たとえば、dcc.Location を監視している場合はこれを使用します。絶対 URL の場合はデフォルトで true であり、それ以外は false です。

  * `header`（ブール; オプション）：これが従来のメニューアイテムではなくヘッダーである場合は True に設定します。
  * `href`（文字列; オプション）：メニューエントリをリンクにするために URL（相対または絶対）を渡します。
  * `key`（文字列; オプション）：コンポーネントの一意の識別子で、コンポーネントをレンダリングする際に React.js のパフォーマンスを向上させるために使用されます。詳細については https://reactjs.org/docs/lists-and-keys.html を参照してください。
  * `loading_state`（オプション）：dash-renderer からのローディング状態オブジェクトを保持するオブジェクト。loading*state は次のタイプを持ちます：要素 'is*loading'、'prop*name'、'component*name' を含むリスト。

これらの要素は次のタイプを持ちます：

  * `is_loading`（ブール; オプション）：コンポーネントがローディング中かどうかを判断します。
  * `prop_name`（文字列; オプション）：どのプロパティがローディング中であるかを保持します。
  * `component_name`（文字列; オプション）：ローディング中のコンポーネントの名前を保持します。
  * `n_clicks`（実数; オプション）：この要素がクリックされた回数を表す整数です。
  * `n_clicks_timestamp`（実数; オプション）：n_clicks が変更された時刻（1970 年以降の ms）を表す整数です。これを使用して、最も最近変更されたボタンを特定できます。
  * `style`（辞書; オプション）：以前に設定されたスタイルを上書きする CSS スタイルを定義します。
  * `target`（文字列; オプション）：リンクに渡すターゲット属性。外部リンクにのみ適用されます。
  * `toggle`（ブール; オプション）：クリック時に DropdownMenu をトグルするかどうか。デフォルト：True。
