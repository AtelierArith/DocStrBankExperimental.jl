```
dbc_modal(;kwargs...)
dbc_modal(children::Any;kwargs...)
dbc_modal(children_maker::Function;kwargs...)
```

モーダルコンポーネント。モーダルコンポーネントを使用してトグル可能なダイアログを作成します。`is_open`プロパティで可視性を切り替えます。キーワード引数：

  * `children`（ダッシュコンポーネント、文字列、または数値のリストまたは単一; オプション）：このコンポーネントの子要素
  * `id`（文字列; オプション）：このコンポーネントのIDで、ダッシュコンポーネントを識別するために使用されます

コールバック内で。IDはアプリ内のすべてのコンポーネントで一意である必要があります。

  * `autoFocus`（Bool; オプション）：**非推奨** `autofocus`を代わりに使用してください

```
初期化時にモーダルにフォーカスを当てます。
```

  * `autofocus`（Bool; オプション）：初期化時にモーダルにフォーカスを当てます。
  * `backdrop`（Bool | 'static'と等しい値; オプション）：モーダルバックドロップ要素を含めます。代わりに、クリックでモーダルを閉じない

バックドロップのために'static'を指定します。

  * `backdropClassName`（文字列; オプション）：**非推奨** `backdrop_class_name`を代わりに使用してください

バックドロップに適用するCSSクラス。

  * `backdrop_class_name`（文字列; オプション）：バックドロップに適用するCSSクラス。
  * `centered`（Bool; オプション）：trueの場合、ページ上でモーダルを垂直に中央に配置します。
  * `className`（文字列; オプション）：**非推奨** `class_name`を代わりに使用してください。

一般的なプロパティを持つ要素をスタイルするためにCSSと一緒に使用されます。

  * `class_name`（文字列; オプション）：一般的なプロパティを持つ要素をスタイルするためにCSSと一緒に使用されます。
  * `contentClassName`（文字列; オプション）：**非推奨** `content_class_name`を代わりに使用してください

モーダルコンテンツに適用するCSSクラス。

  * `content_class_name`（文字列; オプション）：モーダルコンテンツに適用するCSSクラス。
  * `fade`（Bool; オプション）：モーダルが単に表示されるようにするにはfalseに設定します。
  * `fullscreen`（値は：PropTypes.bool、PropTypes.oneOf(['sm-down', 'md-down', 'lg-down', 'xl-down', 'xxl-down']); オプション）：フルスクリーンモーダルをレンダリングします。ブレークポイントを指定すると、ブレークポイントサイズ未満でモーダルがフルスクリーンとしてレンダリングされます。
  * `is_open`（Bool; オプション）：モーダルが現在開いているかどうか。
  * `keyboard`（Bool; オプション）：エスケープキーが押されたときにモーダルを閉じます。
  * `labelledBy`（文字列; オプション）：**非推奨** `labelledby`を代わりに使用してください

ARIA labelledby属性

  * `labelledby`（文字列; オプション）：ARIA labelledby属性
  * `modalClassName`（文字列; オプション）：**非推奨** `modal_class_name`を代わりに使用してください

モーダルに適用するCSSクラス。

  * `modal_class_name`（文字列; オプション）：モーダルに適用するCSSクラス。
  * `role`（文字列; オプション）：ARIAロール属性。
  * `scrollable`（Bool; オプション）：trueの場合、画面に収まりきらないときにモーダル全体ではなくモーダルボディをスクロールします。
  * `size`（文字列; オプション）：モーダルのサイズを設定します。小、中、大のモーダル用にsm、lg、xlのオプション、またはデフォルトサイズのために未定義のままにします。
  * `style`（辞書; オプション）：以前に設定されたスタイルを上書きするCSSスタイルを定義します。
  * `tag`（文字列; オプション）：モーダルに使用するHTMLタグ、デフォルト：div
  * `zIndex`（実数 | 文字列; オプション）：**非推奨** `zindex`を代わりに使用してください

モーダルのz-indexを設定します。デフォルト1050。

  * `zindex`（実数 | 文字列; オプション）：モーダルのz-indexを設定します。デフォルト1050。
