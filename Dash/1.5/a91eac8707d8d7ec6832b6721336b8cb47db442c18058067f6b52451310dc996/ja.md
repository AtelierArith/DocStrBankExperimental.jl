```
html_img(;kwargs...)
html_img(children::Any, kwargs...)
html_img(children_maker::Function, kwargs...)
```

ImgコンポーネントImgは、<img> HTML5要素のラッパーです。詳細な属性情報については、https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img を参照してください。

  * `children`（ダッシュコンポーネント、文字列、または数値のリストまたは単一; オプション）：このコンポーネントの子要素
  * `id`（String; オプション）：このコンポーネントのIDで、ダッシュコンポーネントを識別するために使用されます。

コールバック内で。IDはアプリ内のすべてのコンポーネントで一意である必要があります。

  * `accessKey`（String; オプション）：要素をアクティブにしたり、フォーカスを追加するためのキーボードショートカット。
  * `alt`（String; オプション）：画像が表示できない場合の代替テキスト。
  * `aria-*`（String; オプション）：ワイルドカードaria属性
  * `className`（String; オプション）：一般的なプロパティを持つ要素をスタイル設定するためにCSSと共に使用されることが多い。
  * `contentEditable`（String; オプション）：要素の内容が編集可能かどうかを示します。
  * `contextMenu`（String; オプション）：要素のコンテキストメニューとして機能する<menu>要素のIDを定義します。
  * `crossOrigin`（String; オプション）：要素がクロスオリジンリクエストをどのように処理するか
  * `data-*`（String; オプション）：ワイルドカードデータ属性
  * `dir`（String; オプション）：テキストの方向を定義します。許可される値は、ltr（左から右）またはrtl（右から左）です。
  * `disable_n_clicks`（Bool; オプション）：Trueの場合、これはn_clicksプロパティを無効にします。これを使用して、スクリーンリーダーに干渉する可能性のあるイベントリスナーを削除します。
  * `draggable`（String; オプション）：要素がドラッグ可能かどうかを定義します。
  * `height`（String; オプション）：ここにリストされている要素の高さを指定します。他のすべての要素については、CSSのheightプロパティを使用します。注意：<div>のような一部のインスタンスでは、これはレガシー属性であり、その場合はCSSのheightプロパティを代わりに使用する必要があります。
  * `hidden`（'hidden', 'HIDDEN' | Bool; オプション）：指定された要素のレンダリングを防ぎ、子要素（例：スクリプト要素）をアクティブに保ちます。
  * `key`（String; オプション）：コンポーネントの一意の識別子で、コンポーネントをレンダリングする際にReact.jsによってパフォーマンスを向上させるために使用されます。詳細については、https://reactjs.org/docs/lists-and-keys.html を参照してください。
  * `lang`（String; オプション）：要素で使用される言語を定義します。
  * `loading_state`（要素を含むリストはis*loading、prop*name、component*name - `is*loading`（Bool; オプション）：コンポーネントが読み込まれているかどうかを判断します -`prop*name`（String; オプション）：どのプロパティが読み込まれているかを保持します -`component*name`（String; オプション）：読み込まれているコンポーネントの名前を保持します; オプション）：dash-rendererからの読み込み状態オブジェクトを保持するオブジェクト
  * `n_clicks`（オプション）：この要素がクリックされた回数を表す整数です。
  * `n_clicks_timestamp`（オプション）：n_clicksが変更された時刻（1970年以降のミリ秒）を表す整数です。
  * `referrerPolicy`（String; オプション）：リソースを取得する際に送信されるリファラーを指定します。
  * `role`（String; オプション）：支援技術によって使用される要素の明示的な役割を定義します。
  * `sizes`（String; オプション）
  * `spellCheck`（String; オプション）：要素に対してスペルチェックが許可されているかどうかを示します。
  * `src`（String; オプション）：埋め込み可能なコンテンツのURL。
  * `srcSet`（String; オプション）：1つ以上のレスポンシブ画像候補。
  * `style`（Dict; オプション）：以前に設定されたスタイルを上書きするCSSスタイルを定義します。
  * `tabIndex`（String; オプション）：ブラウザのデフォルトのタブ順序を上書きし、代わりに指定された順序に従います。
  * `title`（String; オプション）：要素にマウスオーバーしたときにツールチップに表示されるテキスト。
  * `useMap`（String; オプション）
  * `width`（String; オプション）：ここにリストされている要素の幅を確立します。注意：<div>のような他のすべてのインスタンスについては、これはレガシー属性であり、その場合はCSSのwidthプロパティを代わりに使用する必要があります。

```
