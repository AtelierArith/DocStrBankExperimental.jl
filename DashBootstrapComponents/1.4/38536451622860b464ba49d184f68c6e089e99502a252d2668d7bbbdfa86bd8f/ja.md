```
dbc_popover(;kwargs...)
dbc_popover(children::Any;kwargs...)
dbc_popover(children_maker::Function;kwargs...)
```

ポップオーバーコンポーネント。ポップオーバーは、ユーザーに追加情報やコンテンツを提供するために使用できるトグル可能なオーバーレイを作成します。新しいページを読み込んだり、新しいウィンドウを開いたりする必要はありません。

`PopoverHeader`および`PopoverBody`コンポーネントを使用して、子要素のレイアウトを制御します。キーワード引数：

  * `children`（リストまたは単一のダッシュコンポーネント、文字列または数値; オプション）：このコンポーネントの子要素
  * `id`（String; オプション）：このコンポーネントのIDで、ダッシュコンポーネントをコールバックで識別するために使用されます。IDはアプリ内のすべてのコンポーネントで一意である必要があります。
  * `autohide`（Bool; オプション）：コンテンツにホバーしているときにポップオーバーをオプションで非表示にします - デフォルトはFalse。
  * `body`（Bool; オプション）：bodyが`True`の場合、ポップオーバーはすべての子要素を自動的に`PopoverBody`にレンダリングします。
  * `className`（String; オプション）：**非推奨** `class_name`を代わりに使用してください。

一般的に、共通のプロパティを持つ要素のスタイルを設定するためにCSSと一緒に使用されます。

  * `class_name`（String; オプション）：一般的に、共通のプロパティを持つ要素のスタイルを設定するためにCSSと一緒に使用されます。
  * `delay`（オプション）：表示/非表示の遅延をオプションで上書きします。delayは次の型を持ちます：'show'、'hide'を含むリスト。

これらの要素は次の型を持ちます：

  * `show`（Real; オプション）
  * `hide`（Real; オプション） | Real
  * `flip`（Bool; オプション）：ポップオーバーがコンテナの端に近すぎる場合に方向を反転させるかどうか、デフォルトはTrue。
  * `hide_arrow`（Bool; オプション）：ポップオーバーの矢印を非表示にします。
  * `innerClassName`（String; オプション）：**非推奨** `inner_class_name`を代わりに使用してください。

ポップオーバーに適用するCSSクラス。

  * `inner_class_name`（String; オプション）：ポップオーバーに適用するCSSクラス。
  * `is_open`（Bool; オプション）：ポップオーバーが開いているかどうか。
  * `key`（String; オプション）：コンポーネントの一意の識別子で、コンポーネントをレンダリングする際にReact.jsによってパフォーマンスを向上させるために使用されます。詳細についてはhttps://reactjs.org/docs/lists-and-keys.htmlを参照してください。
  * `loading_state`（オプション）：dash-rendererからのローディング状態オブジェクトを保持するオブジェクト。loading*stateは次の型を持ちます：'is*loading'、'prop*name'、'component*name'を含むリスト。

これらの要素は次の型を持ちます：

  * `is_loading`（Bool; オプション）：コンポーネントがローディング中かどうかを判断します。
  * `prop_name`（String; オプション）：どのプロパティがローディング中かを保持します。
  * `component_name`（String; オプション）：ローディング中のコンポーネントの名前を保持します。
  * `offset`（String | Real; オプション）：ターゲットに対するポップオーバーのオフセット。オフセットは、カンマ区切りの値のペアとして渡すことができます。例："0,8"。最初の数値、スキディングは、参照要素に沿ってポップオーバーを移動させます。2番目の数値、距離は、ポップオーバーを参照要素から遠ざけるか、または近づける方向に移動させます。正の数値はさらに遠くに移動させ、負の数値は参照要素と重なるようにします。詳細についてはhttps://popper.js.org/docs/v2/modifiers/offset/を参照してください。

または、単一の'distance'数値（例：8）を提供して水平方向に移動させることもできます。

  * `persisted_props`（値が'is_open'に等しい配列; オプション）：ユーザーの操作がコンポーネントまたはページをリフレッシュした後も持続するプロパティ。通常、このプロパティは無視できます。
  * `persistence`（Bool | String | Real; オプション）：このコンポーネントでのユーザーの操作を、コンポーネントまたはページがリフレッシュされたときに持続させるために使用されます。`persisted`が真で、以前の値から変更されていない場合、アプリを使用している間にユーザーが変更した`value`は、その変更を保持します。新しい`value`が元々与えられたものと一致する限りです。`persistence_type`と一緒に使用されます。
  * `persistence_type`（値が：'local'、'session'、'memory'に等しい; オプション）：持続したユーザーの変更が保存される場所：

memory：メモリ内にのみ保持され、ページリフレッシュ時にリセットされます。local：window.localStorage、ブラウザを終了した後もデータが保持されます。session：window.sessionStorage、ブラウザを終了した後にデータがクリアされます。

  * `placement`（値が：'auto'、'auto-start'、'auto-end'、'top'、'top-start'、'top-end'、'right'、'right-start'、'right-end'、'bottom'、'bottom-start'、'bottom-end'、'left'、'left-start'、'left-end'に等しい; オプション）：ポップオーバーの配置を指定します。
  * `style`（Dict; オプション）：以前に設定されたスタイルを上書きするCSSスタイルを定義します。
  * `target`（String | Dict; オプション）：ポップオーバーを接続するコンポーネントのID。
  * `trigger`（String; オプション）：トリガーのスペース区切りリスト（例："click hover focus legacy"）。これらは、ターゲットコンポーネントがポップオーバーをトグルする方法を指定します。指定しない場合は、コールバックを使用して自分でポップオーバーをトグルする必要があります。オプションは次のとおりです：
  * "click"：ターゲットがクリックされたときにポップオーバーをトグルします。
  * "hover"：ターゲットにカーソルを合わせたときにポップオーバーをトグルします。
  * "focus"：ターゲットがフォーカスを受け取ったときにポップオーバーをトグルします。
  * "legacy"：ターゲットがクリックされたときにポップオーバーをトグルしますが、ユーザーがポップオーバーの外をクリックしたときにポップオーバーを閉じます。
