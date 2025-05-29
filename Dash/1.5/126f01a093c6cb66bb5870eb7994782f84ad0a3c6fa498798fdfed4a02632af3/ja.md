```
dcc_markdown(;kwargs...)
dcc_markdown(children::Any, kwargs...)
dcc_markdown(children_maker::Function, kwargs...)
```

A Markdown component GitHub Markdown仕様に従ってMarkdownテキストをレンダリングするコンポーネントです。これらのコンポーネントは、内部で[react-markdown](https://rexxars.github.io/react-markdown/)を使用しています。

  * `children` (String | Array of Strings; optional): CommonMark仕様に従ったマークダウン文字列（または文字列の配列）
  * `id` (String; optional): このコンポーネントのIDで、ダッシュコンポーネントをコールバックで識別するために使用されます。このIDは、アプリ内のすべてのコンポーネントで一意である必要があります。
  * `className` (String; optional): コンテナ要素のクラス名
  * `dangerously_allow_html` (Bool; optional): 生のHTMLエスケープを制御するためのブール値。

コードからHTMLを設定することはリスクが高く、ユーザーをクロスサイトスクリプティング（XSS）(https://en.wikipedia.org/wiki/Cross-site_scripting)攻撃にさらす可能性があります。

  * `dedent` (Bool; optional): すべての行から一致する先頭の空白を削除します。

空の行や*のみ*空白を含む行は無視されます。スペースとタブ文字は削除されますが、一致する場合のみです。タブをスペースに変換したり、その逆を行ったりすることはありません。

  * `highlight_config` (lists containing elements theme   - `theme` ('dark', 'light'; optional): カラースキーム; デフォルトは'light'; optional): 構文ハイライトのための設定オプション。
  * `link_target` (String; optional): リンクに使用するターゲット属性のための文字列（例: "_blank"）
  * `loading_state` (lists containing elements is*loading, prop*name, component*name   - `is*loading`(Bool; optional): コンポーネントが読み込み中かどうかを判断します   -`prop*name`(String; optional): どのプロパティが読み込み中かを保持します   -`component*name` (String; optional): 読み込み中のコンポーネントの名前を保持します; optional): dash-rendererからの読み込み状態オブジェクトを保持するオブジェクト
  * `mathjax` (Bool; optional): trueの場合、ページにmathjax v3 (tex-svg)を読み込み、マークダウンで使用します
  * `style` (Dict; optional): レンダリングされたMarkdownのためのユーザー定義のインラインスタイル
