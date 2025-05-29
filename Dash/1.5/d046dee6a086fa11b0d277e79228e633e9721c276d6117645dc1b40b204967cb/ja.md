```
dcc_input(;kwargs...)
```

入力コンポーネント テキスト、数字、またはパスワードを入力するための基本的なHTML入力コントロールです。

チェックボックスおよびラジオタイプは、ChecklistおよびRadioItemsコンポーネントを通じてサポートされています。日付、時間、およびファイルアップロードも別のコンポーネントを通じてサポートされています。

  * `id` (String; optional): このコンポーネントのIDで、コールバック内でダッシュコンポーネントを識別するために使用されます。

IDはアプリ内のすべてのコンポーネントで一意である必要があります。

  * `autoComplete` (String; optional): この属性は、コントロールの値がブラウザによって自動的に完了できるかどうかを示します。
  * `autoFocus` ('autoFocus', 'autofocus', 'AUTOFOCUS' | Bool; optional): ページが読み込まれた後、要素が自動的にフォーカスされるべきです。

autoFocusはHTMLのブール属性であり、ブール値または'autoFocus'によって有効になります。代替の大文字小文字 `autofocus` & `AUTOFOCUS` も受け入れられます。

  * `className` (String; optional): 入力要素のクラス
  * `debounce` (Bool; optional): trueの場合、入力の変更はEnterキーを押すか、フォーカスを失ったときのみDashサーバーに送信されます。

falseの場合、変更のたびに値が送信されます。

  * `disabled` ('disabled', 'DISABLED' | Bool; optional): trueの場合、入力は無効になり、クリックできません。

disabledはHTMLのブール属性であり、ブール値または'disabled'によって有効になります。代替の大文字小文字 `DISABLED`

  * `inputMode` ('verbatim', 'latin', 'latin-name', 'latin-prose', 'full-width-latin', 'kana', 'katakana', 'numeric', 'tel', 'email', 'url'; optional): ユーザーが要素またはその内容を編集しているときに入力される可能性のあるデータのタイプに関するヒントをブラウザに提供します。
  * `list` (String; optional): ユーザーに提案する事前定義されたオプションのリストを識別します。

値は同じドキュメント内の<datalist>要素のIDでなければなりません。ブラウザはこの入力要素の有効な値であるオプションのみを表示します。この属性は、type属性の値がhidden、checkbox、radio、file、またはボタンタイプの場合は無視されます。

  * `loading_state` (要素を含むリスト is*loading, prop*name, component*name   - `is*loading`(Bool; optional): コンポーネントが読み込まれているかどうかを判断します   -`prop*name`(String; optional): どのプロパティが読み込まれているかを保持します   -`component*name` (String; optional): 読み込まれているコンポーネントの名前を保持します; optional): dash-rendererからの読み込み状態オブジェクトを保持するオブジェクト
  * `max` (String; optional): このアイテムの最大（数値または日付時刻）値で、最小（min属性）値より小さくてはなりません。
  * `maxLength` (String; optional): type属性の値がtext、email、search、password、tel、またはurlの場合、この属性はユーザーが入力できる最大文字数（UTF-16コードユニット）を指定します。他のコントロールタイプの場合は無視されます。size属性の値を超えることができます。指定されていない場合、ユーザーは無制限の文字数を入力できます。負の数を指定すると、デフォルトの動作（すなわち、ユーザーは無制限の文字数を入力できる）になります。制約は属性の値が変更されたときのみ評価されます。
  * `min` (String; optional): このアイテムの最小（数値または日付時刻）値で、最大（max属性）値より大きくてはなりません。
  * `minLength` (String; optional): type属性の値がtext、email、search、password、tel、またはurlの場合、この属性はユーザーが入力できる最小文字数（Unicodeコードポイント）を指定します。他のコントロールタイプの場合は無視されます。
  * `multiple` (Bool; optional): このブール属性は、ユーザーが複数の値を入力できるかどうかを示します。この属性はtype属性がemailまたはfileに設定されている場合に適用され、それ以外の場合は無視されます。
  * `n_blur` (optional): 入力がフォーカスを失った回数。
  * `n_blur_timestamp` (optional): 入力が最後にフォーカスを失った時間。
  * `n_submit` (optional): 入力がフォーカスを持っている間に`Enter`キーが押された回数。
  * `n_submit_timestamp` (optional): 最後に`Enter`が押された時間。
  * `name` (String; optional): コントロールの名前で、フォームデータと共に送信されます。
  * `pattern` (String; optional): コントロールの値がチェックされる正規表現。パターンは全体の値と一致する必要があり、一部のサブセットだけではありません。ユーザーを助けるためにパターンを説明するためにtitle属性を使用します。この属性は、type属性の値がtext、search、tel、url、email、またはpasswordの場合に適用され、それ以外の場合は無視されます。正規表現言語はJavaScript RegExpアルゴリズムと同じで、'u'パラメータがあり、パターンをUnicodeコードポイントのシーケンスとして扱います。パターンはスラッシュで囲まれていません。
  * `persisted_props` (Array of 'value's; optional): ユーザーの操作がコンポーネントまたはページをリフレッシュした後も持続するプロパティ。通常、このプロパティは`value`のみが許可されるため、無視できます。
  * `persistence` (Bool | String; optional): このコンポーネント内のユーザーの操作を、コンポーネントまたはページがリフレッシュされたときに持続させるために使用されます。`persisted`が真であり、以前の値から変更されていない場合、アプリを使用している間にユーザーが変更した`value`は、その変更を保持します。新しい`value`が元の値と一致する限りです。`persistence_type`と組み合わせて使用されます。
  * `persistence_type` ('local', 'session', 'memory'; optional): 持続されたユーザーの変更が保存される場所：

memory: メモリ内にのみ保持され、ページリフレッシュ時にリセットされます。local: window.localStorage、ブラウザを終了した後もデータが保持されます。session: window.sessionStorage、ブラウザを終了するとデータがクリアされます。

  * `placeholder` (String; optional): コントロールに何を入力できるかについてのユーザーへのヒント。プレースホルダーテキストにはキャリッジリターンや改行を含めてはいけません。注意: <label>要素の代わりにplaceholder属性を使用しないでください。目的が異なります。<label>属性はフォーム要素の役割を説明します（すなわち、どのような情報が期待されるかを示します）、プレースホルダー属性はコンテンツが取るべき形式についてのヒントです。プレースホルダー属性がユーザーに表示されない場合があるため、フォームはそれなしでも理解可能でなければなりません。
  * `readOnly` (Bool | 'readOnly', 'readonly', 'READONLY'; optional): この属性は、ユーザーがコントロールの値を変更できないことを示します。属性の値は無関係です。入力値に対して読み書きアクセスが必要な場合は、"readonly"属性を追加しないでください。type属性の値がhidden、range、color、checkbox、radio、file、またはボタンタイプ（ボタンや送信など）の場合は無視されます。

readOnlyはHTMLのブール属性であり、ブール値または'readOnly'によって有効になります。代替の大文字小文字 `readonly` & `READONLY` も受け入れられます。

  * `required` ('required', 'REQUIRED' | Bool; optional): この属性は、ユーザーがフォームを送信する前に値を入力する必要があることを指定します。type属性がhidden、image、またはボタンタイプ（submit、reset、またはbutton）の場合は使用できません。:optionalおよび:required CSS擬似クラスは、適切にフィールドに適用されます。

requiredはHTMLのブール属性であり、ブール値または'required'によって有効になります。代替の大文字小文字 `REQUIRED` も受け入れられます。

  * `selectionDirection` (String; optional): 選択が行われた方向。この値は、選択がLTRロケールで左から右に、またはRTLロケールで右から左に行われた場合は"forward"、逆の方向で行われた場合は"backward"です。選択が行われた方向が不明なプラットフォームでは、この値は"none"になることがあります。たとえば、macOSでは、デフォルトの方向は"none"であり、ユーザーがキーボードを使用して選択を変更し始めると、この値は選択が拡大する方向を反映するように変わります。
  * `selectionEnd` (String; optional): 最後に選択された文字の要素のテキストコンテンツ内のオフセット。選択がない場合、この値は現在のテキスト入力カーソル位置の次の文字のオフセットを示します（つまり、次に入力される文字が占める位置）。
  * `selectionStart` (String; optional): 最初に選択された文字の要素のテキストコンテンツ内のオフセット。選択がない場合、この値は現在のテキスト入力カーソル位置の次の文字のオフセットを示します（つまり、次に入力される文字が占める位置）。
  * `size` (String; optional): コントロールの初期サイズ。この値はピクセル単位ですが、type属性の値がtextまたはpasswordの場合は文字数の整数になります。これ以降、この属性はtype属性がtext、search、tel、url、email、またはpasswordに設定されている場合にのみ適用され、それ以外の場合は無視されます。さらに、サイズはゼロより大きくなければなりません。サイズを指定しない場合、デフォルト値20が使用されます。'ユーザーエージェントは、少なくともその数の文字が表示されることを保証する必要があります'と単に述べていますが、特定のフォントでは異なる文字が異なる幅を持つ場合があります。一部のブラウザでは、x文字の特定の文字列が、サイズが少なくともxに定義されていても完全には表示されないことがあります。
  * `spellCheck` ('true', 'false' | Bool; optional): この属性の値をtrueに設定すると、要素のスペルと文法をチェックする必要があることを示します。値のデフォルトは、要素が親要素のspellcheck値に基づいてデフォルトの動作を行うことを示します。値falseは、要素がチェックされるべきではないことを示します。
  * `step` (String; optional): minおよびmax属性と連携して、数値または日付時刻値が設定できる増分を制限します。anyという文字列または正の浮動小数点数であることができます。この属性がanyに設定されていない場合、コントロールは最小値より大きいstep値の倍数の値のみを受け入れます。
  * `style` (Dict; optional): 入力のインラインスタイル
  * `type` ('text', 'number', 'password', 'email', 'range', 'search', 'tel', 'url', 'hidden'; optional): 描画するコントロールのタイプ。
  * `value` (String; optional): 入力の値

```
