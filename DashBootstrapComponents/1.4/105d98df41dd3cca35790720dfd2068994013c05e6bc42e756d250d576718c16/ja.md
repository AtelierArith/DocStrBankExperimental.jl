```
dbc_input(;kwargs...)
```

入力コンポーネント。テキスト、数字、またはパスワードを入力するための基本的なHTML入力コントロールで、Bootstrapスタイルが自動的に適用されます。このコンポーネントは、dash*core*componentsの対応物に非常に似ていますが、ユーザーフィードバックを提供するための`valid`および`invalid`プロパティなど、いくつかの追加機能があります。

チェックボックスおよびラジオタイプは、ChecklistおよびRadioItemsコンポーネントを通じてサポートされています。日付、時刻、およびファイルアップロードは、他のライブラリの別のコンポーネントを通じてサポートされています。キーワード引数：

  * `id` (String; optional): このコンポーネントのIDで、コールバック内でダッシュコンポーネントを識別するために使用されます。

アプリ内のすべてのコンポーネントで一意である必要があります。

  * `autoComplete` (String; optional): **非推奨** `autocomplete`を代わりに使用してください。

この属性は、コントロールの値がブラウザによって自動的に完了できるかどうかを示します。

  * `autoFocus` (a value equal to: 'autoFocus', 'autofocus', 'AUTOFOCUS' | Bool; optional): **非推奨** `autofocus`を代わりに使用してください。

ページが読み込まれた後、要素が自動的にフォーカスされるべきです。autoFocusはHTMLのブール属性であり、ブール値または'autoFocus'によって有効になります。代替の大文字小文字`autofocus`および`AUTOFOCUS`も受け入れられます。

  * `autocomplete` (String; optional): この属性は、コントロールの値がブラウザによって自動的に完了できるかどうかを示します。
  * `autofocus` (a value equal to: 'autoFocus', 'autofocus', 'AUTOFOCUS' | Bool; optional): ページが読み込まれた後、要素が自動的にフォーカスされるべきです。

autoFocusはHTMLのブール属性であり、ブール値または'autoFocus'によって有効になります。代替の大文字小文字`autofocus`および`AUTOFOCUS`も受け入れられます。

  * `className` (String; optional): **非推奨** `class_name`を代わりに使用してください。

一般的に、共通のプロパティを持つ要素をスタイルするためにCSSと共に使用されます。

  * `class_name` (String; optional): 一般的に、共通のプロパティを持つ要素をスタイルするためにCSSと共に使用されます。
  * `debounce` (Bool; optional): trueの場合、入力の変更は、Enterキーが押されたときまたはコンポーネントがフォーカスを失ったときにのみDashサーバーに送信されます。 falseの場合、変更のたびに値が送信されます。
  * `disabled` (Bool; optional): 入力を無効にするにはTrueに設定します。
  * `html_size` (String; optional): コントロールの初期サイズ。この値はピクセル単位で、type属性の値がtextまたはpasswordの場合は、文字数の整数になります。この属性は、type属性がtext、search、tel、url、email、またはpasswordに設定されている場合にのみ適用され、それ以外の場合は無視されます。さらに、サイズはゼロより大きくなければなりません。サイズを指定しない場合、デフォルト値20が使用されます。
  * `inputMode` (a value equal to: "verbatim", "latin", "latin-name", "latin-prose", "full-width-latin", "kana", "katakana", "numeric", "tel", "email", "url"; optional): **非推奨** `inputmode`を代わりに使用してください。

要素またはその内容を編集している間にユーザーが入力する可能性のあるデータのタイプについて、ブラウザにヒントを提供します。

  * `inputmode` (a value equal to: "verbatim", "latin", "latin-name", "latin-prose", "full-width-latin", "kana", "katakana", "numeric", "tel", "email", "url"; optional): ユーザーが要素またはその内容を編集している間に入力する可能性のあるデータのタイプについて、ブラウザにヒントを提供します。
  * `invalid` (Bool; optional): フィードバック目的でInputに無効スタイルを適用します。これにより、valid=Falseの囲むdiv内のFormFeedbackが表示されます。
  * `key` (String; optional): コンポーネントの一意の識別子で、コンポーネントをレンダリングする際にReact.jsによってパフォーマンスを向上させるために使用されます。詳細については、https://reactjs.org/docs/lists-and-keys.htmlを参照してください。
  * `list` (String; optional): ユーザーに提案するための事前定義されたオプションのリストを識別します。

値は、同じドキュメント内の<datalist>要素のIDでなければなりません。ブラウザは、この入力要素の有効な値であるオプションのみを表示します。この属性は、type属性の値がhidden、checkbox、radio、file、またはボタンタイプの場合は無視されます。

  * `loading_state` (optional): dash-rendererからのローディング状態オブジェクトを保持するオブジェクト。loading*stateは次のタイプを持ちます：要素'is*loading'、'prop*name'、'component*name'を含むリスト。

これらの要素は次のタイプを持ちます：

  * `is_loading` (Bool; optional): コンポーネントが読み込まれているかどうかを判断します。
  * `prop_name` (String; optional): どのプロパティが読み込まれているかを保持します。
  * `component_name` (String; optional): 読み込まれているコンポーネントの名前を保持します。
  * `max` (String | Real; optional): このアイテムの最大（数値または日付時刻）値で、最小（min属性）値より小さくてはなりません。
  * `maxLength` (String | Real; optional): **非推奨** `maxlength`を代わりに使用してください。

type属性の値がtext、email、search、password、tel、またはurlの場合、この属性はユーザーが入力できる最大文字数（UTF-16コードユニット単位）を指定します。他のコントロールタイプの場合は無視されます。サイズ属性の値を超えることができます。指定しない場合、ユーザーは無制限の文字数を入力できます。負の数を指定すると、デフォルトの動作（すなわち、ユーザーは無制限の文字数を入力できる）になります。制約は、属性の値が変更されたときにのみ評価されます。

  * `maxlength` (String | Real; optional): type属性の値がtext、email、search、password、tel、

またはurlの場合、この属性はユーザーが入力できる最大文字数（UTF-16コードユニット単位）を指定します。他のコントロールタイプの場合は無視されます。サイズ属性の値を超えることができます。指定しない場合、ユーザーは無制限の文字数を入力できます。負の数を指定すると、デフォルトの動作（すなわち、ユーザーは無制限の文字数を入力できる）になります。制約は、属性の値が変更されたときにのみ評価されます。

  * `min` (String | Real; optional): このアイテムの最小（数値または日付時刻）値で、最大（max属性）値より大きくてはなりません。
  * `minLength` (String | Real; optional): **非推奨** `minlength`を代わりに使用してください。

type属性の値がtext、email、search、password、tel、またはurlの場合、この属性はユーザーが入力できる最小文字数（Unicodeコードポイント単位）を指定します。他のコントロールタイプの場合は無視されます。

  * `minlength` (String | Real; optional): type属性の値がtext、email、search、password、tel、

またはurlの場合、この属性はユーザーが入力できる最小文字数（Unicodeコードポイント単位）を指定します。他のコントロールタイプの場合は無視されます。

  * `n_blur` (Real; optional): 入力がフォーカスを失った回数。
  * `n_blur_timestamp` (Real; optional): 入力がフォーカスを失った最後の時間。
  * `n_submit` (Real; optional): 入力がフォーカスを持っている間に`Enter`キーが押された回数。
  * `n_submit_timestamp` (Real; optional): `Enter`が押された最後の時間。
  * `name` (String; optional): フォームデータと共に送信されるコントロールの名前。
  * `pattern` (String; optional): コントロールの値がチェックされる正規表現。パターンは、部分集合だけでなく、全体の値と一致する必要があります。ユーザーを助けるために、パターンを説明するためにtitle属性を使用してください。この属性は、type属性の値がtext、search、tel、url、email、またはpasswordの場合に適用され、それ以外の場合は無視されます。正規表現言語は、'u'パラメータを持つJavaScript RegExpアルゴリズムと同じであり、パターンをUnicodeコードポイントのシーケンスとして扱います。パターンはスラッシュで囲まれていません。
  * `persisted_props` (Array of a value equal to: 'value's; optional): コンポーネントまたはページを更新した後もユーザーの操作が持続するプロパティ。通常、このプロパティは`value`のみが許可されるため、無視できます。
  * `persistence` (Bool | String | Real; optional): コンポーネントまたはページが更新されたときに、このコンポーネント内のユーザーの操作を持続させるために使用されます。`persisted`が真であり、以前の値から変更されていない場合、アプリを使用している間にユーザーが変更した`value`は、その変更を保持します。新しい`value`が元の値と一致する限りです。`persistence_type`と共に使用されます。
  * `persistence_type` (a value equal to: 'local', 'session', 'memory'; optional): 持続したユーザーの変更が保存される場所：

memory: メモリ内にのみ保持され、ページ更新時にリセットされます。local: window.localStorage、ブラウザを終了した後もデータが保持されます。session: window.sessionStorage、ブラウザを終了するとデータがクリアされます。

  * `placeholder` (String | Real; optional): コントロールに入力できる内容のヒント。プレースホルダーテキストにはキャリッジリターンや改行を含めてはいけません。注意：<label>要素の代わりにplaceholder属性を使用しないでください。目的が異なります。<label>属性はフォーム要素の役割を説明します（すなわち、どのような情報が期待されるかを示します）、プレースホルダ属性は、コンテンツが取るべき形式についてのヒントです。プレースホルダ属性がユーザーに表示されない場合があるため、フォームはそれなしでも理解できる必要があります。
  * `plaintext` (Bool; optional): デフォルトのフォームフィールドスタイリングを削除し、正しいマージンとパディングを保持したプレーンテキストとしてスタイルされた入力にtrueを設定します。通常、これはreadonly=Trueと共に使用することをお勧めします。
  * `readonly` (Bool | a value equal to: 'readOnly', 'readonly', 'READONLY'; optional): 要素が編集可能かどうかを示します。
  * `required` (a value equal to: 'required', 'REQUIRED' | Bool; optional): この属性は、ユーザーがフォームを送信する前に値を入力する必要があることを指定します。type属性がhidden、image、またはボタンタイプ（submit、reset、またはbutton）の場合には使用できません。:optionalおよび:required CSS擬似クラスは、適切にフィールドに適用されます。requiredはHTMLのブール属性であり、ブール値または'required'によって有効になります。代替の大文字小文字`REQUIRED`も受け入れられます。
  * `size` (String; optional): 入力のサイズを設定します。オプション：'sm'（小）、'md'（中）

または'lg'（大）。デフォルトは'md'です。

  * `step` (String | Real; optional): minおよびmax属性と共に、数値または日付時刻値を設定できる増分を制限します。文字列anyまたは正の浮動小数点数であることができます。この属性がanyに設定されていない場合、コントロールは最小値より大きいstep値の倍数の値のみを受け入れます。
  * `style` (Dict; optional): 以前に設定されたスタイルを上書きするCSSスタイルを定義します。
  * `tabIndex` (String; optional): **非推奨** `tabindex`を代わりに使用してください。

ブラウザのデフォルトのタブ順序を上書きし、指定された順序に従います。

  * `tabindex` (String; optional): ブラウザのデフォルトのタブ順序を上書きし、指定された順序に従います。
  * `type` (a value equal to: "text", 'number', 'password', 'email', 'range', 'search', 'tel', 'url', 'hidden'; optional): レンダリングするコントロールのタイプ
  * `valid` (Bool; optional): フィードバック目的でInputに有効スタイルを適用します。これにより、valid=Trueの囲むdiv内のFormFeedbackが表示されます。
  * `value` (String | Real; optional): Inputの値

```
