```
dcc_textarea(;kwargs...)
```

テキストエリアコンポーネント 基本的なHTMLテキストエリアで、複数行のテキストを入力します。

  * `id` (String; optional): このコンポーネントのIDで、コールバック内でダッシュコンポーネントを識別するために使用されます。

アプリ内のすべてのコンポーネントで一意である必要があります。

  * `accessKey` (String; optional): 要素をアクティブにしたり、フォーカスを追加するためのキーボードショートカットを定義します。
  * `autoFocus` (String; optional): ページが読み込まれた後に自動的に要素にフォーカスを当てるべきです。
  * `className` (String; optional): 共通のプロパティを持つ要素をスタイル設定するためにCSSと一緒に使用されることが多いです。
  * `cols` (String; optional): テキストエリアの列数を定義します。
  * `contentEditable` (String | Bool; optional): 要素の内容が編集可能かどうかを示します。
  * `contextMenu` (String; optional): 要素のコンテキストメニューとして機能する<menu>要素のIDを定義します。
  * `dir` (String; optional): テキストの方向を定義します。許可される値は、ltr（左から右）またはrtl（右から左）です。
  * `disabled` (String | Bool; optional): ユーザーが要素と対話できるかどうかを示します。
  * `draggable` ('true', 'false' | Bool; optional): 要素がドラッグ可能かどうかを定義します。
  * `form` (String; optional): 要素の所有者であるフォームを示します。
  * `hidden` (String; optional): 指定された要素のレンダリングを防ぎますが、子要素（例：スクリプト要素）はアクティブのままにします。
  * `lang` (String; optional): 要素で使用される言語を定義します。
  * `loading_state` (要素を含むリスト is*loading, prop*name, component*name   - `is*loading`(Bool; optional): コンポーネントが読み込まれているかどうかを判断します   -`prop*name`(String; optional): どのプロパティが読み込まれているかを保持します   -`component*name` (String; optional): 読み込まれているコンポーネントの名前を保持します; optional): dash-rendererからの読み込み状態オブジェクトを保持するオブジェクト
  * `maxLength` (String; optional): 要素に許可される最大文字数を定義します。
  * `minLength` (String; optional): 要素に許可される最小文字数を定義します。
  * `n_blur` (optional): テキストエリアがフォーカスを失った回数。
  * `n_blur_timestamp` (optional): テキストエリアが最後にフォーカスを失った時間。
  * `n_clicks` (optional): テキストエリアがクリックされた回数。
  * `n_clicks_timestamp` (optional): テキストエリアが最後にクリックされた時間。
  * `name` (String; optional): 要素の名前。サーバーがフォーム送信時にフィールドを識別するために使用されます。
  * `persisted_props` (Array of 'value's; optional): ユーザーの対話がコンポーネントまたはページをリフレッシュした後も持続するプロパティ。通常、`value`のみが許可されるため、このプロパティは無視できます。
  * `persistence` (Bool | String; optional): コンポーネントまたはページがリフレッシュされたときに、このコンポーネントでのユーザーの対話を持続させるために使用されます。`persisted`が真であり、以前の値から変更されていない場合、ユーザーがアプリを使用中に変更した`value`は、その変更を保持します。新しい`value`が元々与えられたものと一致する限り。`persistence_type`と一緒に使用されます。
  * `persistence_type` ('local', 'session', 'memory'; optional): 持続されたユーザーの変更が保存される場所：

memory: メモリ内にのみ保持され、ページリフレッシュ時にリセットされます。 local: window.localStorage、データはブラウザを終了した後も保持されます。 session: window.sessionStorage、データはブラウザを終了するとクリアされます。

  * `placeholder` (String; optional): フィールドに何を入力できるかのヒントをユーザーに提供します。
  * `readOnly` (Bool | 'readOnly', 'readonly', 'READONLY'; optional): 要素が編集可能かどうかを示します。

readOnlyはHTMLのブール属性です - ブール値または'readOnly'によって有効になります。代替の大文字表記`readonly` & `READONLY`も受け入れられます。

  * `required` ('required', 'REQUIRED' | Bool; optional): この要素が記入必須かどうかを示します。

requiredはHTMLのブール属性です - ブール値または'required'によって有効になります。代替の大文字表記`REQUIRED`も受け入れられます。

  * `rows` (String; optional): テキストエリアの行数を定義します。
  * `spellCheck` ('true', 'false' | Bool; optional): 要素に対してスペルチェックが許可されているかどうかを示します。
  * `style` (Dict; optional): 以前に設定されたスタイルを上書きするCSSスタイルを定義します。
  * `tabIndex` (String; optional): ブラウザのデフォルトのタブ順序を上書きし、代わりに指定された順序に従います。
  * `title` (String; optional): 要素にマウスをホバーしたときにツールチップに表示されるテキスト。
  * `value` (String; optional): テキストエリアの値
  * `wrap` (String; optional): テキストを折り返すべきかどうかを示します。
