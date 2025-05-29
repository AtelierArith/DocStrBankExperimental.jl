```
dbc_navlink(;kwargs...)
dbc_navlink(children::Any;kwargs...)
dbc_navlink(children_maker::Function;kwargs...)
```

NavLinkコンポーネント。`Nav`にリンクを追加します。`NavItem`の子として、または`Nav`の子として直接使用できます。キーワード引数：

  * `children`（ダッシュコンポーネント、文字列、または数値のリストまたは単一のもの; オプション）：このコンポーネントの子
  * `id`（文字列; オプション）：このコンポーネントのIDで、ダッシュコンポーネントを識別するために使用されます。

コールバック内で。IDはアプリ内のすべてのコンポーネントで一意である必要があります。

  * `active`（Bool | 'partial'、'exact'と等しい値; オプション）：このコンポーネントに'active'スタイルを適用します。現在のパス名がhrefと一致する場合に自動的にアクティブ状態を切り替えるには"exact"に設定するか、部分一致で自動的に切り替えるには"partial"に設定します。hrefは、https://example.com/linkのような絶対URLではなく、/linkのような相対URLであると仮定します。

例えば

  * dbc.NavLink(..., href="/my-page", active="exact")は"/my-page"でアクティブになりますが、"/my-page/other"や"/random"ではアクティブになりません。
  * dbc.NavLink(..., href="/my-page", active="partial")は"/my-page"と"/my-page/other"でアクティブになりますが、"/random"ではアクティブになりません。
  * `className`（文字列; オプション）：**非推奨** `class_name`を代わりに使用してください。

共通のプロパティを持つ要素をスタイル設定するためにCSSと一緒に使用されることが多いです。

  * `class_name`（文字列; オプション）：共通のプロパティを持つ要素をスタイル設定するためにCSSと一緒に使用されることが多いです。
  * `disabled`（Bool; オプション）：リンクを無効にします。
  * `external_link`（Bool; オプション）：trueの場合、ブラウザはこれを外部リンクとして扱い、

新しい場所でページをリフレッシュします。falseの場合、これはページをリフレッシュせずに場所を変更するだけです。例えば、dcc.Locationを監視している場合にこれを使用します。絶対URLの場合はtrueがデフォルトで、それ以外はfalseです。

  * `href`（文字列; オプション）：リンクされたリソースのURL。
  * `key`（文字列; オプション）：コンポーネントの一意の識別子で、コンポーネントをレンダリングする際にReact.jsによってパフォーマンスを向上させるために使用されます。詳細についてはhttps://reactjs.org/docs/lists-and-keys.htmlを参照してください。
  * `loading_state`（オプション）：dash-rendererからのローディング状態オブジェクトを保持するオブジェクト。loading*stateは次の型を持ちます：要素'is*loading'、'prop*name'、'component*name'を含むリスト。

これらの要素は次の型を持ちます：

  * `is_loading`（Bool; オプション）：コンポーネントがロード中かどうかを判断します。
  * `prop_name`（文字列; オプション）：どのプロパティがロード中かを保持します。
  * `component_name`（文字列; オプション）：ロード中のコンポーネントの名前を保持します。
  * `n_clicks`（実数; オプション）：この要素がクリックされた回数を表す整数です。
  * `n_clicks_timestamp`（実数; オプション）：n_clicksが変更された時刻（1970年からのミリ秒）を表す整数です。これを使用して、どのボタンが最近変更されたかを判断できます。
  * `style`（辞書; オプション）：以前に設定されたスタイルを上書きするCSSスタイルを定義します。
  * `target`（文字列; オプション）：リンクに渡すターゲット属性。外部リンクにのみ適用されます。
