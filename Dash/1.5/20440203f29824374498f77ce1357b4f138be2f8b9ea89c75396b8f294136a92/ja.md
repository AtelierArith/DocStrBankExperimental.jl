```
dcc_loading(;kwargs...)
dcc_loading(children::Any, kwargs...)
dcc_loading(children_maker::Function, kwargs...)
```

ローディングコンポーネント 他のコンポーネントをラップし、ラップされたコンポーネントがレンダリングされるまでスピナーを表示するローディングコンポーネント。

  * `children` (配列のリストまたは単一のダッシュコンポーネント、文字列または数字 | リストまたは単一のダッシュコンポーネント、文字列または数字; オプション): レンダリングするコンポーネントを保持する配列
  * `id` (文字列; オプション): このコンポーネントのIDで、ダッシュコンポーネントを識別するために使用される

コールバック内で。IDはアプリ内のすべてのコンポーネントで一意である必要があります。

  * `className` (文字列; オプション): スピナーのルートDOMノードの追加CSSクラス
  * `color` (文字列; オプション): ローディングスピナーに使用される主要な色
  * `debug` (ブール; オプション): trueの場合、スピナーはローディング中にcomponent*nameとprop*nameを表示します
  * `fullscreen` (ブール; オプション): スピナーをフルスクリーンで表示するブール値
  * `loading_state` (要素を含むリストはis*loading、prop*name、component*name   - `is*loading`(ブール; オプション): コンポーネントがローディング中かどうかを判断します   -`prop*name`(文字列; オプション): どのプロパティがローディング中かを保持します   -`component*name` (文字列; オプション): ローディング中のコンポーネントの名前を保持します; オプション): dash-rendererからのローディング状態オブジェクトを保持するオブジェクト
  * `parent_className` (文字列; オプション): 最外層のdcc.Loading親div DOMノードの追加CSSクラス
  * `parent_style` (辞書; オプション): 最外層のdcc.Loading親div DOMノードの追加CSSスタイル
  * `style` (辞書; オプション): スピナーのルートDOMノードの追加CSSスタイル
  * `type` ('graph', 'cube', 'circle', 'dot', 'default'; オプション): どのスピナーを表示するかを決定するプロパティ

'graph'、'cube'、'circle'、'dot'、または'default'のいずれか。
