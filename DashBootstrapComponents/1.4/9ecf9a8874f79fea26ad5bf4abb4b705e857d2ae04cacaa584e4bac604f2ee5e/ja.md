```
dbc_textarea(;kwargs...)
```

テキストエリアコンポーネント。dash-core-componentsの対応するコンポーネントに基づいた、複数行のテキストを入力するための基本的なHTMLテキストエリア。キーワード引数：

  * `id` (String; optional): このコンポーネントのIDで、コールバック内でダッシュコンポーネントを識別するために使用されます。IDはアプリ内のすべてのコンポーネントで一意である必要があります。
  * `accessKey` (String; optional): **非推奨** `accesskey`を代わりに使用してください

要素をアクティブにしたり、フォーカスを追加するためのキーボードショートカットを定義します。

  * `accesskey` (String; optional): 要素をアクティブにしたり、フォーカスを追加するためのキーボードショートカットを定義します。
  * `autoFocus` (String; optional): **非推奨** `autofocus`を代わりに使用してください

ページが読み込まれた後、要素が自動的にフォーカスされるべきです。

  * `autofocus` (String; optional): ページが読み込まれた後、要素が自動的にフォーカスされるべきです。
  * `className` (String; optional): **非推奨** `class_name`を代わりに使用してください。

共通のプロパティを持つ要素をスタイル設定するためにCSSと一緒に使用されることが多いです。

  * `class_name` (String; optional): 共通のプロパティを持つ要素をスタイル設定するためにCSSと一緒に使用されることが多いです。
  * `cols` (String | Real; optional): テキストエリアの列数を定義します。
  * `contentEditable` (String | Real; optional): **非推奨** `contenteditable`を代わりに使用してください

要素の内容が編集可能かどうかを示します。

  * `contenteditable` (String | Real; optional): 要素の内容が編集可能かどうかを示します。
  * `contextMenu` (String; optional): **非推奨** `contextmenu`を代わりに使用してください

要素のコンテキストメニューとして機能する<menu>要素のIDを定義します。

  * `contextmenu` (String; optional): 要素のコンテキストメニューとして機能する<menu>要素のIDを定義します。
  * `debounce` (Bool; optional): trueの場合、入力の変更はEnterキーを押すかフォーカスを失ったときのみDashサーバーに送信されます。

falseの場合、すべての変更で値が送信されます。

  * `dir` (String; optional): テキストの方向を定義します。許可される値はltr（左から右）またはrtl（右から左）です。
  * `disabled` (String | Bool; optional): ユーザーが要素と対話できるかどうかを示します。
  * `draggable` (a value equal to: 'true', 'false' | Bool; optional): 要素がドラッグ可能かどうかを定義します。
  * `form` (String; optional): 要素の所有者であるフォームを示します。
  * `hidden` (String; optional): 指定された要素のレンダリングを防ぎますが、子要素（例：スクリプト要素）はアクティブのままにします。
  * `invalid` (Bool; optional): フィードバック目的でテキストエリアに無効スタイルを適用します。これにより、valid=Falseの囲むdiv内のFormFeedbackが表示されます。
  * `key` (String; optional): コンポーネントの一意の識別子で、コンポーネントをレンダリングする際にReact.jsによってパフォーマンスを向上させるために使用されます。詳細についてはhttps://reactjs.org/docs/lists-and-keys.htmlを参照してください。
  * `lang` (String; optional): 要素で使用される言語を定義します。
  * `loading_state` (optional): dash-rendererからのローディング状態オブジェクトを保持するオブジェクト。loading*stateは次の型を持ちます：要素'is*loading'、'prop*name'、'component*name'を含むリスト。

これらの要素は次の型を持ちます：

  * `is_loading` (Bool; optional): コンポーネントが読み込まれているかどうかを判断します。
  * `prop_name` (String; optional): どのプロパティが読み込まれているかを保持します。
  * `component_name` (String; optional): 読み込まれているコンポーネントの名前を保持します。
  * `maxLength` (String | Real; optional): **非推奨** `maxlength`を代わりに使用してください

要素に許可される最大文字数を定義します。

  * `maxlength` (String | Real; optional): 要素に許可される最大文字数を定義します。
  * `minLength` (String | Real; optional): **非推奨** `minlength`を代わりに使用してください

要素に許可される最小文字数を定義します。

  * `minlength` (String | Real; optional): 要素に許可される最小文字数を定義します。
  * `n_blur` (Real; optional): 入力がフォーカスを失った回数。
  * `n_blur_timestamp` (Real; optional): 入力がフォーカスを失った最後の時間。
  * `n_clicks` (Real; optional): この要素がクリックされた回数を表す整数。
  * `n_clicks_timestamp` (Real; optional): n_clicksが変更された時間（1970年からのミリ秒）を表す整数。これにより、どのボタンが最近変更されたかを知ることができます。
  * `n_submit` (Real; optional): テキストエリアがフォーカスを持っている間に`Enter`キーが押された回数。
  * `n_submit_timestamp` (Real; optional): `Enter`が押された最後の時間。
  * `name` (String; optional): 要素の名前。サーバーがフォーム送信時にフィールドを識別するために使用されます。
  * `persisted_props` (Array of a value equal to: 'value's; optional): コンポーネントまたはページをリフレッシュした後もユーザーの対話が持続するプロパティ。通常、`value`のみが許可されるため、このプロパティは無視されることが多いです。
  * `persistence` (Bool | String | Real; optional): コンポーネントまたはページがリフレッシュされたときに、このコンポーネントでのユーザーの対話を持続させるために使用されます。`persisted`が真で、以前の値から変更されていない場合、アプリを使用している間にユーザーが変更した`value`は、その変更を保持します。新しい`value`が元々与えられたものと一致する限りです。`persistence_type`と一緒に使用されます。
  * `persistence_type` (a value equal to: 'local', 'session', 'memory'; optional): 持続されたユーザーの変更が保存される場所：

memory: メモリ内にのみ保持され、ページリフレッシュ時にリセットされます。 local: window.localStorage、データはブラウザを終了した後も保持されます。 session: window.sessionStorage、データはブラウザを終了するとクリアされます。

  * `placeholder` (String; optional): フィールドに何を入力できるかのヒントをユーザーに提供します。
  * `readOnly` (Bool | a value equal to: 'readOnly', 'readonly', 'READONLY'; optional): **非推奨** `readonly`を代わりに使用してください

要素が編集可能かどうかを示します。

  * `readonly` (Bool | a value equal to: 'readOnly', 'readonly', 'READONLY'; optional): 要素が編集可能かどうかを示します。
  * `required` (a value equal to: 'required', 'REQUIRED' | Bool; optional): この属性は、ユーザーがフォームを送信する前に値を入力する必要があることを指定します。タイプ属性がhidden、image、またはボタンタイプ（submit、reset、またはbutton）の場合には使用できません。:optionalおよび:required CSS擬似クラスは、適切にフィールドに適用されます。requiredはHTMLのブール属性であり、ブール値または'required'によって有効になります。代替の大文字表記`REQUIRED`も受け入れられます。
  * `rows` (String | Real; optional): テキストエリアの行数を定義します。
  * `size` (String; optional): テキストエリアのサイズを設定します。有効なオプションは'sm'、'md'、または'lg'です。
  * `spellCheck` (a value equal to: 'true', 'false' | Bool; optional): **非推奨** `spellcheck`を代わりに使用してください

要素に対してスペルチェックが許可されているかどうかを示します。

  * `spellcheck` (a value equal to: 'true', 'false' | Bool; optional): 要素に対してスペルチェックが許可されているかどうかを示します。
  * `style` (Dict; optional): 以前に設定されたスタイルを上書きするCSSスタイルを定義します。
  * `tabIndex` (String | Real; optional): **非推奨** `tabindex`を代わりに使用してください

ブラウザのデフォルトのタブ順序を上書きし、指定された順序に従います。

  * `tabindex` (String | Real; optional): ブラウザのデフォルトのタブ順序を上書きし、指定された順序に従います。
  * `title` (String; optional): 要素にマウスオーバーしたときにツールチップに表示されるテキスト。
  * `valid` (Bool; optional): フィードバック目的でテキストエリアに有効スタイルを適用します。これにより、valid=Trueの囲むdiv内のFormFeedbackが表示されます。
  * `value` (String; optional): テキストエリアの値
  * `wrap` (String; optional): テキストが折り返されるべきかどうかを示します。
