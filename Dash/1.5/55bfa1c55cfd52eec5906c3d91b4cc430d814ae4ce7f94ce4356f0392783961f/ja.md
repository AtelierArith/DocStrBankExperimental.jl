```
html_dt(;kwargs...)
html_dt(children::Any, kwargs...)
html_dt(children_maker::Function, kwargs...)
```

A Dt コンポーネント Dt は、<dt> HTML5 要素のラッパーです。詳細な属性情報については、https://developer.mozilla.org/en-US/docs/Web/HTML/Element/dt を参照してください。

  * `children` (ダッシュコンポーネント、文字列、または数値のリストまたは単一; オプション): このコンポーネントの子要素
  * `id` (String; オプション): このコンポーネントの ID で、ダッシュコンポーネントを識別するために使用されます

コールバック内で。ID はアプリ内のすべてのコンポーネントで一意である必要があります。

  * `accessKey` (String; オプション): 要素をアクティブにしたり、フォーカスを追加するためのキーボードショートカット。
  * `aria-*` (String; オプション): ワイルドカード aria 属性
  * `className` (String; オプション): 一般的なプロパティを持つ要素にスタイルを適用するために CSS と共に使用されることが多いです。
  * `contentEditable` (String; オプション): 要素の内容が編集可能かどうかを示します。
  * `contextMenu` (String; オプション): 要素のコンテキストメニューとして機能する <menu> 要素の ID を定義します。
  * `data-*` (String; オプション): ワイルドカードデータ属性
  * `dir` (String; オプション): テキストの方向を定義します。許可される値は ltr (左から右) または rtl (右から左) です。
  * `disable_n_clicks` (Bool; オプション): True の場合、これは n_clicks プロパティを無効にします。これを使用して、スクリーンリーダーに干渉する可能性のあるイベントリスナーを削除します。
  * `draggable` (String; オプション): 要素がドラッグ可能かどうかを定義します。
  * `hidden` ('hidden', 'HIDDEN' | Bool; オプション): 指定された要素のレンダリングを防ぎますが、子要素（例: スクリプト要素）はアクティブのままにします。
  * `key` (String; オプション): コンポーネントの一意の識別子で、コンポーネントをレンダリングする際に React.js によってパフォーマンスを向上させるために使用されます。詳細については https://reactjs.org/docs/lists-and-keys.html を参照してください。
  * `lang` (String; オプション): 要素で使用される言語を定義します。
  * `loading_state` (要素を含むリスト is*loading, prop*name, component*name   - `is*loading`(Bool; オプション): コンポーネントが読み込まれているかどうかを判断します   -`prop*name`(String; オプション): どのプロパティが読み込まれているかを保持します   -`component*name` (String; オプション): 読み込まれているコンポーネントの名前を保持します; オプション): dash-renderer からの読み込み状態オブジェクトを保持するオブジェクト
  * `n_clicks` (オプション): この要素がクリックされた回数を表す整数です。
  * `n_clicks_timestamp` (オプション): n_clicks が変更された時刻（1970 年以降の ms 単位）を表す整数です。

これを使用して、どのボタンが最近変更されたかを判断できます。

  * `role` (String; オプション): 補助技術によって使用される要素の明示的な役割を定義します。
  * `spellCheck` (String; オプション): 要素に対してスペルチェックが許可されているかどうかを示します。
  * `style` (Dict; オプション): 以前に設定されたスタイルを上書きする CSS スタイルを定義します。
  * `tabIndex` (String; オプション): ブラウザのデフォルトのタブ順序を上書きし、代わりに指定された順序に従います。
  * `title` (String; オプション): 要素の上にカーソルを置いたときにツールチップに表示されるテキスト。
