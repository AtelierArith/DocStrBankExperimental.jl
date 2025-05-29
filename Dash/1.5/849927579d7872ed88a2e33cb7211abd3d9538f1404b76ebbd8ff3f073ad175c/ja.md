```
dash_datatable(;kwargs...)
```

Dash DataTableコンポーネントは、大規模なデータセットを表示、編集、探索するために設計されたインタラクティブなテーブルコンポーネントです。DataTableは、標準的で意味的なHTML <table/> マークアップでレンダリングされるため、アクセシブルで、レスポンシブで、スタイルを適用しやすくなっています。このコンポーネントは、Dashコミュニティのために特にReact.jsでゼロから書かれました。そのAPIは人間工学に基づいて設計されており、その動作はプロパティを通じて完全にカスタマイズ可能です。

  * `id` (String; optional): テーブルのID。
  * `active_cell` (要素を含むリスト row, column, row*id, column*id   - `row` (optional)   - `column` (optional)   - `row_id` (String; optional)   - `column_id` (String; optional); optional): 現在アクティブなセルの行と列のインデックスおよびID。

`row_id`は、データ行に`id`キーがある場合にのみ返されます。

  * `cell_selectable` (Bool; optional): True（デフォルト）の場合、テーブルセルをクリックしてナビゲートすることが可能です。
  * `column_selectable` ('single', 'multi', false; optional): `single`の場合、ユーザーはラジオボタンを介して単一の列またはマージされた列のグループを選択できます。`multi`の場合、ユーザーはチェックボックスを介して複数の列またはマージされた列のグループを選択できます。falseの場合、ユーザーは列を選択できず、ヘッダー行に入力は表示されません。列が選択されると、そのIDは`selected_columns`および`derived_viewport_selected_columns`に含まれます。
  * `columns` (optional): 列は各個別の列に関するさまざまな側面を説明します。

`name`と`id`が唯一の必須パラメータです。columnsは次の型を持ちます: 要素を含むリストの配列 id, name, type, presentation, selectable, clearable, deletable, editable, hideable, renamable, filter*options, format, on*change, sort*as*null, validation   - `id` (String; required): 列の`id`。列の`id`は、データ内のセルを特定の列に一致させるために使用されます。`id`はテーブル内では表示されません。   - `name` (String | Array of Strings; required): 列の`name`、列ヘッダーに表示されるように。`name`が文字列のリストの場合、列は複数のヘッダー行でレンダリングされます。   - `type` ('any', 'numeric', 'text', 'datetime'; optional): データ型は、列ごとの型付けをサポートし、データの検証と強制を可能にします。 'numeric': 浮動小数点数と整数の両方を表します。 'text': 文字列を表します。 'datetime': 日付または日付時刻を表す文字列で、形式は次の通りです:   'YYYY-MM-DD HH:MM:SS.ssssss' またはその一部の切り捨て。年は4桁でなければなりませんが、`validation.allow_YY: true`を使用する場合は例外です。また、日付と時刻の間に'T'または't'を受け入れ、最後にタイムゾーン情報を許可します。これらの文字列をPythonの`datetime`オブジェクトに変換するには、`dateutil.parser.isoparse`を使用します。Rでは、`parsedate`ライブラリの`parse_iso_8601`を使用します。   警告: これらのパーサーは2桁の年には機能しません。`validation.allow_YY: true`を使用し、4桁の年に強制しない場合です。また、2桁の年で機能するパーサーは、フロントエンドで行う推測とは異なる世紀を推測する可能性があります。 'any': 任意のデータ型を表します。未定義の場合は'any'がデフォルトです。   - `presentation` ('input', 'dropdown', 'markdown'; optional): データを表示するために使用する`presentation`。タイプ'text'の列にはMarkdownを使用できます。  詳細については'dropdown'を参照してください。デフォルトは['datetime', 'numeric', 'text', 'any']のために'input'です。   - `selectable` ('first', 'last' | Bool | Array of Bools; optional): Trueの場合、ユーザーは列をチェックボックスまたはラジオボタンをクリックして選択できます。複数のヘッダー行がある場合、trueは各行に入力を表示します。`last`の場合、入力は最後のヘッダー行にのみ表示されます。`first`の場合、最初のヘッダー行にのみ表示されます。これらはそれぞれ`[false, ..., false, true]`および`[true, false, ..., false]`のショートカットに相当します。マージされたマルチヘッダー列がある場合、ブール値の配列を提供することで、どの列ヘッダー行に入力を表示するかを選択できます。たとえば、`[true, false]`は最初の行に`selectable`入力を表示しますが、2行目には表示しません。`selectable`入力がマージされた列に表示される場合、その入力をクリックすると、それに関連するすべてのマージされた列が選択されます。テーブルレベルのプロパティ`column_selectable`は、使用する列選択のタイプを決定するために使用されます。   - `clearable` ('first', 'last' | Bool | Array of Bools; optional): Trueの場合、ユーザーは列の`clear`アクションボタンをクリックして列をクリアできます。複数のヘッダー行がある場合、trueは各行にアクションボタンを表示します。`last`の場合、`clear`アクションボタンは最後のヘッダー行にのみ表示されます。`first`の場合、最初のヘッダー行にのみ表示されます。これらはそれぞれ`[false, ..., false, true]`および`[true, false, ..., false]`のショートカットに相当します。マージされたマルチヘッダー列がある場合、ブール値の配列を提供することで、どの列ヘッダー行に`clear`アクションボタンを表示するかを選択できます。たとえば、`[true, false]`は最初の行に`clear`アクションボタンを表示しますが、2行目には表示しません。`clear`アクションボタンがマージされた列に表示される場合、そのボタンをクリックすると、それに関連するすべてのマージされた列がクリアされます。`column.deletable`とは異なり、このアクションはテーブルから列を削除しません。関連するエントリを`data`から削除するだけです。   - `deletable` ('first', 'last' | Bool | Array of Bools; optional): Trueの場合、ユーザーは列の`delete`アクションボタンをクリックして列を削除できます。複数のヘッダー行がある場合、trueは各行にアクションボタンを表示します。`last`の場合、`delete`アクションボタンは最後のヘッダー行にのみ表示されます。`first`の場合、最初のヘッダー行にのみ表示されます。これらはそれぞれ`[false, ..., false, true]`および`[true, false, ..., false]`のショートカットに相当します。マージされたマルチヘッダー列がある場合、ブール値の配列を提供することで、どの列ヘッダー行に`delete`アクションボタンを表示するかを選択できます。たとえば、`[true, false]`は最初の行に`delete`アクションボタンを表示しますが、2行目には表示しません。`delete`アクションボタンがマージされた列に表示される場合、そのボタンをクリックすると、それに関連するすべてのマージされた列が削除されます。   - `editable` (Bool; optional): テーブルには2つの`editable`フラグがあります。これは列レベルのeditableフラグであり、テーブルレベルの`editable`フラグもあります。これらのフラグは、テーブルの内容が編集可能かどうかを決定します。列レベルの`editable`フラグが設定されている場合、その列のテーブルレベルの`editable`フラグを上書きします。   - `hideable` ('first', 'last' | Bool | Array of Bools; optional): Trueの場合、ユーザーは列の`hide`アクションボタンをクリックして列を隠すことができます。複数のヘッダー行がある場合、trueは各行にアクションボタンを表示します。`last`の場合、`hide`アクションボタンは最後のヘッダー行にのみ表示されます。`first`の場合、最初のヘッダー行にのみ表示されます。これらはそれぞれ`[false, ..., false, true]`および`[true, false, ..., false]`のショートカットに相当します。マージされたマルチヘッダー列がある場合、ブール値の配列を提供することで、どの列ヘッダー行に`hide`アクションボタンを表示するかを選択できます。たとえば、`[true, false]`は最初の行に`hide`アクションボタンを表示しますが、2行目には表示しません。`hide`アクションボタンがマージされた列に表示される場合、そのボタンをクリックすると、それに関連するすべてのマージされた列が隠されます。   - `renamable` ('first', 'last' | Bool | Array of Bools; optional): Trueの場合、ユーザーは列の`rename`アクションボタンをクリックして列の名前を変更できます。複数のヘッダー行がある場合、trueは各行にアクションボタンを表示します。`last`の場合、`rename`アクションボタンは最後のヘッダー行にのみ表示されます。`first`の場合、最初のヘッダー行にのみ表示されます。これらはそれぞれ`[false, ..., false, true]`および`[true, false, ..., false]`のショートカットに相当します。マージされたマルチヘッダー列がある場合、ブール値の配列を提供することで、どの列ヘッダー行に`rename`アクションボタンを表示するかを選択できます。たとえば、`[true, false]`は最初の行に`rename`アクションボタンを表示しますが、2行目には表示しません。`rename`アクションボタンがマージされた列に表示される場合、そのボタンをクリックすると、それに関連するすべてのマージされた列の名前が変更されます。   - `filter_options` (要素を含むリスト case, placeholder*text   - `case` ('sensitive', 'insensitive'; optional): (default: 'sensitive') 適用可能なフィルタ関係演算子が`sensitive`または`insensitive`比較のデフォルトになるかどうかを決定します。   - `placeholder*text`(String; optional): (default: 'filter data...') フィルタセルのプレースホルダーテキスト。; optional): テーブルには2つの`filter*options`プロパティがあります。これは列レベルのfilter*optionsプロパティであり、テーブルレベルの`filter_options`プロパティもあります。列レベルの`filter_options`プロパティが設定されている場合、その列のテーブルレベルの`filter_options`プロパティを上書きします。   - `format` (optional): 列のデータに適用されるフォーマット。このプロパティは、[d3-format](https://github.com/d3/d3-format)ライブラリの仕様から派生しています。構造がわずかに異なる（単一のプロパティの下にある）以外は、使用法は同じです。dash*table.FormatTemplateも参照してください。典型的な数値フォーマットのためのヘルパー関数が含まれています。formatは次の型を持ちます: 要素を含むリスト locale, nully, prefix, specifier   - `locale` (optional): ローカライズ特有のフォーマット情報を表します。指定しない場合、d3-formatによって提供されるデフォルト値が使用されます。localeは次の型を持ちます: 要素を含むリストの配列 symbol, decimal, group, grouping, numerals, percent, separate*4digits   - `symbol` (Array of Strings; optional): (default: ['$', '']).  プレフィックスとサフィックスシンボルを表す2つの文字列のリスト。通常は通貨に使用され、d3の通貨フォーマットを使用して実装されていますが、測定単位などの他のシンボルにも使用できます。   - `decimal` (String; optional): (default: '.').  小数点区切りに使用される文字列   - `group` (String; optional): (default: ',').  グループ区切りに使用される文字列   - `grouping` (Array of s; optional): (default: [3]).  グループ化パターンを表す整数のリスト。デフォルトは千のための3です。   - `numerals` (Array of Strings; optional): 数字0-9の置き換えに使用される10の文字列のリスト   - `percent` (String; optional): (default: '%').  パーセンテージシンボルに使用される文字列   - `separate_4digits` (Bool; optional): (default: True).  4桁以下の整数を区切ります   - `nully` (Bool | Real | String | Dict | Array; optional): フォーマット中にnully値の代わりに使用される値。値の型が列の型と一致する場合、通常通りフォーマットされます。   - `prefix` (optional): フォーマット中に使用するSI単位を表す数値。   有効な値のリストについては`dash_table.Format.Prefix`列挙を参照してください。   - `specifier` (String; optional): (default: '').  数値をフォーマットする際に適用されるd3ルールを表します。   - `on_change` (optional): ユーザーによる変更のための列の`on_change`動作。on*changeは次の型を持ちます: 要素を含むリスト action, failure   - `action` ('coerce', 'none', 'validate'; optional): (default 'coerce'):  'none': データを検証しない;  'coerce': データが宛先型に対応しているか確認し、そうでない場合は宛先型に強制しようとする;  'validate': データが宛先型に対応しているか確認する（強制なし）。   - `failure` ('accept', 'default', 'reject'; optional): (default 'reject'):  アクションが失敗した場合の値の扱い。  'accept': 無効な値を使用する;  'default': 提供された値を`validation.default`で置き換える;  'reject': 既存の値を変更しない。   - `sort*as*null`(Array of String | Bools; optional): ソート時に`null`（すなわち無視され、常に最後に表示される）として扱われる文字列、数値、ブール値の配列。この値はテーブルレベルの`sort*as*null`を上書きします。   -`validation`(optional): ユーザー入力処理のための`validation`オプションで、受け入れ、拒否、またはデフォルト値を適用できます。validationは次の型を持ちます: 要素を含むリスト allow*null, default, allow*YY   - `allow*null`(Bool; optional): nully値の使用を許可します。 (undefined, null, NaN) (default: False)   -`default`(Bool | Real | String | Dict | Array; optional):`on*change.failure = 'default'`で適用されるデフォルト値。(default: None)   -`allow*YY`(Bool; optional): これは`datetime`列のみに適用されます。  2桁の年を許可します（default: False）。   Trueの場合、年は今から70年から今から29年の範囲と解釈されます - 2019年には1949年から2048年ですが、2020年には異なります。`action: 'coerce'`と一緒に使用される場合、ユーザー入力を4桁の年に変換します。

  * `css` (要素を含むリスト selector, rule   - `selector` (String; required)   - `rule` (String; required)s; optional): `css`プロパティは、CSSセレクタとルールをページに埋め込む方法です。`css`プロパティを使用する前に、`style_*`プロパティから始めることをお勧めします。例: [     {"selector": ".dash-spreadsheet", "rule": 'font-family: "monospace"'} ]
  * `data` (Array of Dict with Strings as keys and values of type String | Bools; optional): テーブルの内容。

data内の各アイテムのキーは列のIDと一致する必要があります。各アイテムには'id'キーも持つことができ、その値は行IDです。ID='id'の列がある場合、これが行IDを表示します。そうでない場合は、選択、フィルタリングなどのために行を参照するために使用されます。例: [      {'column-1': 4.5, 'column-2': 'montreal', 'column-3': 'canada'},      {'column-1': 8, 'column-2': 'boston', 'column-3': 'america'} ]

  * `data_previous` (Array of Dicts; optional): `data`の前の状態。`data_previous`

は`data`と同じ構造を持ち、`data`が変更されるたびに更新されます。これは読み取り専用のプロパティです。このプロパティを設定してもテーブルには影響しません。

  * `data_timestamp` (optional): データが最後に編集されたときのUnixタイムスタンプ。

このプロパティを他のタイムスタンププロパティ（`dash_html_components`の`n_clicks_timestamp`など）と一緒に使用して、コールバック内でどのプロパティが変更されたかを判断します。

  * `derived_filter_query_structure` (Dict; optional): このプロパティは、`filter_query`の現在の構造をツリー構造として表します。クエリ構造の各ノードには次のものがあります: type (string; required):   'open-block',   'logical-operator',   'relational-operator',   'unary-operator', または   'expression'; subType (string; optional):   'open-block': '()',   'logical-operator': '&&', '||',   'relational-operator': '=', '>=', '>', '<=', '<', '!=', 'contains',   'unary-operator': '!', 'is bool', 'is even', 'is nil', 'is num', 'is object', 'is odd', 'is prime', 'is str',   'expression': 'value', 'field'; value (any):   'expression, value': 渡された値,   'expression, field': フィールド/プロパティ名。 block (ネストされたクエリ構造; optional)。 left (ネストされたクエリ構造; optional)。 right (ネストされたクエリ構造; optional)。クエリが無効または空の場合、`derived_filter_query_structure`は`None`になります。
  * `derived_viewport_data` (Array of Dicts; optional): このプロパティは、現在のページの`data`の現在の状態を表します。このプロパティは、ページング、ソート、フィルタリング時に更新されます。
  * `derived_viewport_indices` (Array of s; optional): `derived_viewport_indices`は、フィルタリング、ソート、および/またはページング後に元の行が表示される順序を示します。`derived_viewport_indices`は現在のページのインデックスを含み、`derived_virtual_indices`はすべてのページのインデックスを含みます。
  * `derived_viewport_row_ids` (Array of Strings; optional): `derived_viewport_row_ids`は、フィルタリング、ソート、および/またはページング後に表示される順序で行IDをリストします。`derived_viewport_row_ids`は現在のページのIDを含み、`derived_virtual_row_ids`はすべてのページのIDを含みます。
  * `derived_viewport_selected_columns` (Array of Strings; optional): `derived_viewport_selected_columns`は、現在非表示でない`selected_columns`のIDを含みます。
  * `derived_viewport_selected_row_ids` (Array of Strings; optional): `derived_viewport_selected_row_ids`は、現在表示されているページの`selected_rows`のIDを表します。
  * `derived_viewport_selected_rows` (Array of s; optional): `derived_viewport_selected_rows`は、`derived_viewport_indices`の観点からの`selected_rows`のインデックスを表します。
  * `derived_virtual_data` (Array of Dicts; optional): このプロパティは、フロントエンドのソートとフィルタリングが適用された後のすべてのページにわたる`data`の可視状態を表します。
  * `derived_virtual_indices` (Array of s; optional): `derived_virtual_indices`は、フィルタリングおよびソート後に元の行が表示される順序を示します。`derived_viewport_indices`は現在のページのインデックスを含み、`derived_virtual_indices`はすべてのページのインデックスを含みます。
  * `derived_virtual_row_ids` (Array of Strings; optional): `derived_virtual_row_ids`は、フィルタリングおよびソート後に表示される順序で行IDを示します。`derived_viewport_row_ids`は現在のページのIDを含み、`derived_virtual_row_ids`はすべてのページのIDを含みます。
  * `derived_virtual_selected_row_ids` (Array of Strings; optional): `derived_virtual_selected_row_ids`は、フィルタリングおよびソート後に表示される`selected_rows`のIDを表します。
  * `derived_virtual_selected_rows` (Array of s; optional): `derived_virtual_selected_rows`は、`derived_virtual_indices`の観点からの`selected_rows`のインデックスを表します。
  * `dropdown` (Dict with Strings as keys and values of type lists containing elements clearable, options   - `clearable` (Bool; optional)   - `options` (Array of lists containing elements label, value   - `label` (String; required)   - `value` (String | Bool; required)s; required); optional): `dropdown`は異なる列のドロップダウンオプションを指定します。

各エントリは列IDを参照します。`clearable`プロパティは、値を削除できるかどうかを定義します。`options`プロパティはドロップダウンの`options`を参照します。

  * `dropdown_conditional` (要素を含むリスト clearable, if, options   - `clearable` (Bool; optional)   - `if` (要素を含むリスト column*id, filter*query   - `column_id` (String; optional)   - `filter_query` (String; optional); optional)   - `options` (Array of lists containing elements label, value   - `label` (String; required)   - `value` (String | Bool; required)s; required)s; optional): `dropdown_conditional`は、さまざまな列およびセルのドロップダウンオプションを指定します。

このプロパティを使用すると、特定の条件に応じて異なるドロップダウンを指定できます。たとえば、"state"列の現在の値に応じて、行内で異なる"city"ドロップダウンをレンダリングすることができます。

  * `dropdown_data` (Array of Dict with Strings as keys and values of type lists containing elements clearable, options   - `clearable` (Bool; optional)   - `options` (Array of lists containing elements label, value   - `label` (String; required)   - `value` (String | Bool; required)s; required)s; optional): `dropdown_data`は、行ごと、列ごとにドロップダウンオプションを指定します。

配列内の各アイテムは、同じインデックスの`data`アイテムに対応するドロップダウンを参照します。アイテム内の各エントリは列IDを参照します。

  * `editable` (Bool; optional): Trueの場合、すべてのセルのデータが編集可能です。

`editable`がTrueの場合、特定の列は`columns`プロパティ内で`editable`をFalseに設定することで編集不可にできます。Falseの場合、すべてのセルのデータは編集不可です。`editable`がFalseの場合、特定の列は`columns`プロパティ内で`editable`をTrueに設定することで編集可能にできます。

  * `end_cell` (要素を含むリスト row, column, row*id, column*id   - `row` (optional)   - `column` (optional)   - `row_id` (String; optional)   - `column_id` (String; optional); optional): 複数のセルを選択する際

（セルをクリックしてから別のセルをシフトクリックすることによって）、`end_cell`は領域の一方の隅にあるセルの行/列の座標とIDを表します。`start_cell`はもう一方の隅の座標を表します。

  * `export_columns` ('all', 'visible'; optional): エクスポートデータファイルで使用される列を示します。

`all`の場合、すべての列が使用されます（表示されている列 + 非表示の列）。`visible`の場合、表示されている列のみが使用されます。デフォルトは`visible`です。

  * `export_format` ('csv', 'xlsx', 'none'; optional): エクスポートデータファイルのタイプを示します。

デフォルトは`'none'`です。

  * `export_headers` ('none', 'ids', 'names', 'display'; optional): エクスポートデータファイルのヘッダーの形式を示します。

`'none'`の場合、ヘッダーは表示されません。`'display'`の場合、データファイルのヘッダーは現在表示されているようになります。`'display'`は`'xlsx'`のexport*formatにのみサポートされ、`'csv'`のexport*formatでは`'names'`のように動作します。`'ids'`または`'names'`の場合、データファイルのヘッダーはそれぞれ列IDまたは列名になります。

  * `fill_width` (Bool; optional): `fill_width`は、2つの一般的な動作のためのCSSのセットを切り替えます。

True: テーブルコンテナの幅は利用可能なスペースを埋めるように成長します; False: テーブルコンテナの幅はその内容の幅と等しくなります。

  * `filter_action` ('custom', 'native', 'none' | 要素を含むリスト type, operator   - `type` ('custom', 'native'; required)   - `operator` ('and', 'or'; optional); optional): `filter_action`プロパティは、`filtering` UIの動作を制御します。

`'none'`の場合、フィルタリングUIは表示されません。`'native'`の場合、フィルタリングUIが表示され、フィルタリングロジックはテーブルによって処理されます。つまり、`data`プロパティに存在するデータに対して実行されます。`'custom'`の場合、フィルタリングUIが表示されますが、フィルタリングをコールバックを通じてプログラムするのは開発者の責任です（`filter_query`または`derived_filter_query_structure`が入力で、`data`が出力になります）。

  * `filter_options` (要素を含むリスト case, placeholder*text   - `case` ('sensitive', 'insensitive'; optional): (default: 'sensitive') 適用可能なフィルタ関係演算子が`sensitive`または`insensitive`比較のデフォルトになるかどうかを決定します。   - `placeholder*text`(String; optional): (default: 'filter data...') フィルタセルのプレースホルダーテキスト。; optional): テーブルには2つの`filter_options`プロパティがあります。

これはテーブルレベルのfilter*optionsプロパティであり、列レベルの`filter*options`プロパティもあります。列レベルの`filter*options`プロパティが設定されている場合、その列のテーブルレベルの`filter*options`プロパティを上書きします。

  * `filter_query` (String; optional): `filter_action`が有効な場合、現在のフィルタリング

文字列はこの`filter_query`プロパティに表されます。

  * `fixed_columns` (要素を含むリスト data, headers   - `data` (0; optional): 例 `{'headers':False, 'data':0}` 固定されている列はありません（デフォルト）   - `headers` (false; optional) | 要素を含むリスト data, headers   - `data` (optional): 例 `{'headers':True, 'data':1}` 1つの列が固定されています。   - `headers` (true; required); optional): `fixed_columns`は、列のセットを「固定」して、固定されていない列を横にスクロールしても表示されるようにします。 `fixed_columns`は左から右に列を固定します。`headers`がFalseの場合、列は固定されません。`headers`がTrueの場合、すべての操作列（`row_deletable`および`row_selectable`を参照）を固定します。追加のデータ列は、`data`に数値を割り当てることで固定できます。列を固定すると、テーブルの基礎となるマークアップにいくつかの変更が加わり、列のレンダリングやサイズに影響を与える可能性があります。詳細については、ドキュメントの例を参照してください。
  * `fixed_rows` (要素を含むリスト data, headers   - `data` (0; optional): 例 `{'headers':False, 'data':0}` 固定されている行はありません（デフォルト）   - `headers` (false; optional) | 要素を含むリスト data, headers   - `data` (optional): 例 `{'headers':True, 'data':1}` 1つの行が固定されています。   - `headers` (true; required); optional): `fixed_rows`は、行のセットを「固定」して、テーブルを垂直にスクロールしても表示されるようにします。 `fixed_rows`は上から下に行を固定します。`headers`がFalseの場合、行は固定されません。`headers`がTrueの場合、すべてのヘッダーおよびフィルタ行（`filter_action`を参照）が固定されます。追加のデータ行は、`data`に数値を割り当てることで固定できます。行を固定すると、テーブルの基礎となるマークアップにいくつかの変更が加わり、列のレンダリングやサイズに影響を与える可能性があります。詳細については、ドキュメントの例を参照してください。
  * `hidden_columns` (Array of Strings; optional): 現在非表示の列の列IDのリスト。

関連するネストされたプロパティ`columns.hideable`を参照してください。

  * `include_headers_on_copy_paste` (Bool; optional): Trueの場合、ヘッダーはテーブルから異なるタブや他の場所にコピーする際に含まれます。テーブルから自身にコピーする場合や、同じタブ内の2つのテーブル間でコピーする場合は、ヘッダーは無視されることに注意してください。
  * `is_focused` (Bool; optional): Trueの場合、`active_cell`はフォーカス状態です。
  * `loading_state` (要素を含むリスト is*loading, prop*name, component*name   - `is*loading`(Bool; optional): コンポーネントが読み込まれているかどうかを決定します   -`prop*name`(String; optional): どのプロパティが読み込まれているかを保持します   -`component*name` (String; optional): 読み込まれているコンポーネントの名前を保持します; optional): dash-rendererからの読み込み状態オブジェクトを保持するオブジェクト
  * `locale_format` (optional): テーブル内のすべての列に適用されるローカライズ特有のフォーマット情報。

このプロパティは、[d3.formatLocale](https://github.com/d3/d3-format#formatLocale)データ構造仕様から派生しています。指定しない場合、各個別のネストされたプロパティは、あらかじめ決められた値にデフォルト設定されます。locale*formatは次の型を持ちます: 要素を含むリスト symbol, decimal, group, grouping, numerals, percent, separate*4digits   - `symbol` (Array of Strings; optional): (default: ['$', '']).  プレフィックスとサフィックスシンボルを表す2つの文字列のリスト。通常は通貨に使用され、d3の通貨フォーマットを使用して実装されていますが、測定単位などの他のシンボルにも使用できます。   - `decimal` (String; optional): (default: '.'). 小数点区切りに使用される文字列。   - `group` (String; optional): (default: ','). グループ区切りに使用される文字列。   - `grouping` (Array of s; optional): (default: [3]). グループ化パターンを表す整数のリスト。   - `numerals` (Array of Strings; optional): 数字0-9の置き換えに使用される10の文字列のリスト。   - `percent` (String; optional): (default: '%'). パーセンテージシンボルに使用される文字列。   - `separate_4digits` (Bool; optional): (default: True).  4桁以下の整数を区切ります。

  * `markdown_options` (optional): `markdown_options`プロパティは、マークダウンセルの動作をカスタマイズすることを可能にします。markdown*optionsは次の型を持ちます: 要素を含むリスト link*target, html   - `link_target` (String | '*blank', '*parent', '*self', '*top'; optional): (default: '*blank').  リンクの動作（*blankはリンクを新しいタブで開き、*parentは親フレームでリンクを開き、*selfは現在のタブでリンクを開き、_topはトップフレームでリンクを開く）または文字列   - `html` (Bool; optional): (default: False)  Trueの場合、htmlはマークダウンセルで使用される可能性があります。信頼できないユーザーからのコンテンツがレンダリングされる可能性がある場合、htmlを有効にする際には注意が必要です。これはXSS脆弱性を引き起こす可能性があります。
  * `merge_duplicate_headers` (Bool; optional): Trueの場合、隣接する重複名の列ヘッダーは1つのセルにマージされます。これは単一列ヘッダーおよびマルチ列ヘッダーに適用されます。
  * `page_action` ('custom', 'native', 'none'; optional): `page_action`は、すべての行が一度に表示されないテーブルのモードを指します: 一部のみが表示され（「ページ」）、次の行の部分はページの下部にある「次へ」または「前へ」ボタンをクリックすることで表示できます。ページネーションはパフォーマンスを向上させるために使用されます: すべての行を一度にレンダリングするのではなく（これは高コストになる可能性があります）、その一部のみを表示します。ページネーションを使用すると、テーブル内に存在するデータをページごとに表示することも（例: `data`内の`10,000`行を`100`行ずつページングする）、ユーザーが「前へ」または「次へ」ボタンをクリックしたときにコールバックでデータを即時更新することもできます。これらのモードは、この`page_action`パラメータで切り替えることができます: `'native'`: すべてのデータが事前にテーブルに渡され、ページングロジックはテーブルによって処理されます; `'custom'`: データは1ページずつテーブルに渡され、ページングロジックはコールバックを介して処理されます; `'none'`: ページングを無効にし、すべてのデータを一度にレンダリングします。
  * `page_count` (optional): `page_count`は、ページネーションされたテーブルのページ数を表します。

これはバックエンドページネーションを行う際にのみ便利です。フロントエンドはテーブルの全サイズを使用してページ数を計算できます。

  * `page_current` (optional): `page_current`は、ユーザーが現在いるページを表します。

このプロパティを使用して、バックエンドページングでコールバック内のデータをインデックス化します。

  * `page_size` (optional): `page_size`は、`page_action`が`'custom'`または`'native'`の場合に特定のページに表示される行数を表します。
  * `persisted_props` (Array of 'columns.name', 'data', 'filter*query', 'hidden*columns', 'page*current', 'selected*columns', 'selected*rows', 'sort*by'; optional): ユーザーの操作がコンポーネントまたはページを更新した後も持続するプロパティ。
  * `persistence` (Bool | String; optional): このコンポーネント内のユーザーの操作を持続させるために使用されます。

コンポーネントまたはページが更新された場合、`persisted`が真であり、以前の値から変更されていない場合、ユーザーがアプリを使用している間に変更した`persisted_props`は、元の値と一致する限り、その変更を保持します。`persistence_type`および`persisted_props`と組み合わせて使用されます。

  * `persistence_type` ('local', 'session', 'memory'; optional): 持続されたユーザーの変更が保存される場所:

memory: メモリ内にのみ保持され、ページ更新時にリセットされます。 local: window.localStorage、ブラウザを終了した後もデータが保持されます。 session: window.sessionStorage、ブラウザを終了するとデータがクリアされます。

  * `row_deletable` (Bool; optional): Trueの場合、各`row`の隣に`x`が表示され、ユーザーは行を削除できます。
  * `row_selectable` ('single', 'multi', false; optional): `single`の場合、ユーザーは各行の隣に表示されるラジオボタンを介して単一の行を選択できます。`multi`の場合、ユーザーは各行の隣に表示されるチェックボックスを介して複数の行を選択できます。falseの場合、ユーザーは行を選択できず、追加のUI要素は表示されません。行が選択されると、そのインデックスは`selected_rows`に含まれます。
  * `selected_cells` (要素を含むリスト row, column, row*id, column*id   - `row` (optional)   - `column` (optional)   - `row_id` (String; optional)   - `column_id` (String; optional)s; optional): `selected_cells`は、選択されたセルのセットを表します。

これは、各アイテムが`active_cell`に似たオブジェクトの配列として表されます。複数のセルを選択するには、シフトを押しながら別のセルをクリックするか、シフトを押しながら矢印キーで移動します。

  * `selected_columns` (Array of Strings; optional): `selected_columns`は、`column_selectable`が`'single'`または`'multi'`のときにUI要素を介して選択された列のIDを含みます。
  * `selected_row_ids` (Array of Strings; optional): `selected_row_ids`は、`row_selectable`が`'single'`または`'multi'`のときにUI要素を介して選択された行のIDを含みます。
  * `selected_rows` (Array of s; optional): `selected_rows`は、`row_selectable`が`'single'`または`'multi'`のときにUI要素を介して選択された行のインデックスを含みます。
  * `sort_action` ('custom', 'native', 'none'; optional): `sort_action`プロパティは、データを列ごとにソートできるようにします。`'none'`の場合、ソートUIは表示されません。`'native'`の場合、ソートUIが表示され、ソートロジックはテーブルによって処理されます。つまり、`data`プロパティに存在するデータに対して実行されます。`'custom'`の場合、ソートUIが表示されますが、ソートをコールバックを介してプログラムするのは開発者の責任です（`sort_by`が入力で、`data`が出力になります）。ソート矢印をクリックすると、`sort_by`プロパティが更新されます。
  * `sort_as_null` (Array of String | Bools; optional): ソート時に`None`（すなわち無視され、常に最後に表示される）として扱われる文字列、数値、ブール値の配列。この値は`sort_as_null`を持たない列で使用されます。デフォルトは`[]`です。
  * `sort_by` (要素を含むリスト column*id, direction   - `column*id`(String; required)   -`direction`('asc', 'desc'; required)s; optional):`sort_by`は現在のソートUIの状態を説明します。

つまり、ユーザーが列のソート矢印をクリックした場合、このプロパティは列IDとソートの方向（`asc`または`desc`）で更新されます。マルチ列ソートの場合、これはクリックされた順序でのソートパラメータのリストになります。

  * `sort_mode` ('single', 'multi'; optional): ソートは複数の列にわたって実行できます

（例: 国でソートし、各国内でソートし、年でソート）または単一の列で実行できます。 注意 - マルチ列ソートでは、現在のところ、UIを介して列がソートされた順序を特定することはできません。 [https://github.com/plotly/dash-table/issues/170](https://github.com/plotly/dash-table/issues/170)を参照してください。

  * `start_cell` (要素を含むリスト row, column, row*id, column*id   - `row` (optional)   - `column` (optional)   - `row_id` (String; optional)   - `column_id` (String; optional); optional): 複数のセルを選択する際

（セルをクリックしてから別のセルをシフトクリックすることによって）、`start_cell`は領域の一方の隅にあるセルの[row, column]座標を表します。`end_cell`はもう一方の隅の座標を表します。

  * `style_as_list_view` (Bool; optional): Trueの場合、テーブルはリストビューのようにスタイルされ、列の間に境界線がありません。
  * `style_cell` (Dict; optional): テーブルの各個別のセルに適用されるCSSスタイル。

これにはヘッダーセル、`data`セル、およびフィルターセルが含まれます。

  * `style_cell_conditional` (要素を含むリスト if   - `if` (要素を含むリスト column*id, column*type   - `column_id` (String | Array of Strings; optional)   - `column_type` ('any', 'numeric', 'text', 'datetime'; optional); optional)s; optional): セルの条件付きCSSスタイル。

これは、列ごとにスタイルを適用するために使用できます。

  * `style_data` (Dict; optional): 各個別のデータセルに適用されるCSSスタイル。

つまり、`style_cell`とは異なり、ヘッダーおよびフィルターセルは除外されます。

  * `style_data_conditional` (要素を含むリスト if   - `if` (要素を含むリスト column*id, column*type, filter*query, state, row*index, column*editable   - `column*id`(String | Array of Strings; optional)   -`column*type`('any', 'numeric', 'text', 'datetime'; optional)   -`filter*query`(String; optional)   -`state`('active', 'selected'; optional)   -`row*index`('odd', 'even' | Array of s; optional)   -`column*editable` (Bool; optional); optional)s; optional): データセルの条件付きCSSスタイル。

これは、列ごとにデータセルにスタイルを適用するために使用できます。

  * `style_filter` (Dict; optional): フィルターセルに適用されるCSSスタイル。

これは、より複雑なフィルタリングUIを構築する際に将来的に変更される可能性があることに注意してください。

  * `style_filter_conditional` (要素を含むリスト if   - `if` (要素を含むリスト column*id, column*type, column*editable   - `column*id`(String | Array of Strings; optional)   -`column*type`('any', 'numeric', 'text', 'datetime'; optional)   -`column*editable` (Bool; optional); optional)s; optional): フィルターセルの条件付きCSSスタイル。

これは、列ごとにフィルターセルにスタイルを適用するために使用できます。

  * `style_header` (Dict; optional): 各個別のヘッダーセルに適用されるCSSスタイル。

つまり、`style_cell`とは異なり、`data`およびフィルターセルは除外されます。

  * `style_header_conditional` (要素を含むリスト if   - `if` (要素を含むリスト column*id, column*type, header*index, column*editable   - `column_id` (String | Array of Strings; optional)   - `column_type` ('any', 'numeric', 'text', 'datetime'; optional)   - `header_index` (Array of s | 'odd', 'even'; optional)   - `column_editable` (Bool; optional); optional)s; optional): ヘッダーセルの条件付きCSSスタイル。

これは、列ごとにヘッダーセルにスタイルを適用するために使用できます。

  * `style_table` (Dict; optional): 外部`table`コンテナに適用されるCSSスタイル。

これは、テーブルの幅や高さなどのプロパティを設定するために一般的に使用されます。

  * `tooltip` (optional): `tooltip`は、すべての行に適用される列ベースのツールチップ設定です。キーは列IDで、値はツールチップ設定です。例: {i: {'value': i, 'use*with: 'both'} for i in df.columns}。 tooltipは次の型を持ちます: Dict with Strings as keys and values of type String | 要素を含むリスト delay, duration, type, use*with, value   - `delay` (optional): セルにホバーしたときにツールチップが表示されるまでの遅延をミリ秒単位で表します。これはテーブルの`tooltip_delay`プロパティを上書きします。`None`に設定すると、ツールチップは即座に表示されます。   - `duration` (optional): セルにホバーしたときにツールチップが表示される期間をミリ秒単位で表します。これはテーブルの`tooltip_duration`プロパティを上書きします。`None`に設定すると、ツールチップは消えません。   - `type` ('text', 'markdown'; optional): ツールチップ生成に使用されるツールチップ構文のタイプを指します。`markdown`または`text`のいずれかです。デフォルトは`text`です。   - `use_with` ('both', 'data', 'header'; optional): ツールチップがデータまたはヘッダーのどちらに表示されるかを指します。`both`、`data`、`header`のいずれかです。デフォルトは`both`です。   - `value` (String; required): ツールチップの構文ベースの内容を指します。この値は必須です。代わりに、プロパティの値はプレーンな文字列でも構いません。この場合、`text`構文が使用されます。
  * `tooltip_conditional` (optional): `tooltip_conditional`は、異なる列およびセルに表示されるツールチップを表します。このプロパティを使用すると、特定の条件に応じて異なるツールチップを指定できます。たとえば、特定のデータプロパティの値に基づいて、同じ列内で異なるツールチップを持つことができます。優先順位は、リスト内で最初から最後まで定義された条件付きツールチップに基づいています。優先順位が高い（より具体的な）条件付きツールチップは、リストの先頭に配置する必要があります。tooltip*conditionalは次の型を持ちます: 要素を含むリスト delay, duration, if, type, value   - `delay` (optional): `delay`は、セルにホバーしたときにツールチップが表示されるまでの遅延をミリ秒単位で表します。これはテーブルの`tooltip*delay`プロパティを上書きします。`None`に設定すると、ツールチップは即座に表示されます。   -`duration`(optional):`duration`は、セルにホバーしたときにツールチップが表示される期間をミリ秒単位で表します。これはテーブルの`tooltip*duration`プロパティを上書きします。`None`に設定すると、ツールチップは消えません。   -`if` (要素を含むリスト column*id, filter*query, row*index   - `column_id` (String; optional): `column_id`は一致させる必要がある列IDを指します。   - `filter_query` (String; optional): `filter_query`はTrueに評価される必要があるクエリを指します。   - `row_index` ('odd', 'even'; optional): `row_index`は、ソース`data`内の行のインデックスを指します。; required): `if`は、関連するツールチップ設定が使用されるために満たす必要がある条件を指します。複数の条件が定義されている場合、すべての条件が満たされる必要があります。   - `type` ('text', 'markdown'; optional): `type`は、ツールチップ生成に使用されるツールチップ構文のタイプを指します。`markdown`または`text`のいずれかです。デフォルトは`text`です。   - `value` (String; required): `value`は、構文ベースのツールチップの内容を指します。この値は必須です。
  * `tooltip_data` (optional): `tooltip_data`は、異なる列およびセルに表示されるツールチップを表します。各キーが列IDで、値がツールチップ設定である辞書のリストです。tooltip*dataは次の型を持ちます: Array of Dict with Strings as keys and values of type String | 要素を含むリスト delay, duration, type, value   - `delay` (optional): `delay`は、セルにホバーしたときにツールチップが表示されるまでの遅延をミリ秒単位で表します。これはテーブルの`tooltip*delay`プロパティを上書きします。`None`に設定すると、ツールチップは即座に表示されます。   -`duration`(optional):`duration`は、セルにホバーしたときにツールチップが表示される期間をミリ秒単位で表します。これはテーブルの`tooltip_duration`プロパティを上書きします。`None`に設定すると、ツールチップは消えません。代わりに、プロパティの値はプレーンな文字列でも構いません。この場合、`text`構文が使用されます。   -`type`('text', 'markdown'; optional): 各ツールチップ設定に対して、`type`はツールチップ生成に使用されるツールチップ構文のタイプを指します。`markdown`または`text`のいずれかです。デフォルトは`text`です。   -`value`(String; required):`value`は、構文ベースのツールチップの内容を指します。この値は必須です。
  * `tooltip_delay` (optional): `tooltip_delay`は、セルにホバーしたときにツールチップが表示されるまでのテーブル全体の遅延をミリ秒単位で表します。`None`に設定すると、ツールチップは即座に表示されます。デフォルトは350です。
  * `tooltip_duration` (optional): `tooltip_duration`は、セルにホバーしたときにツールチップが表示される期間をミリ秒単位で表します。`None`に設定すると、ツールチップは消えません。デフォルトは2000です。
  * `tooltip_header` (optional): `tooltip_header`は、各ヘッダー列およびオプションで各ヘッダー行に表示されるツールチップを表します。長い列名をツールチップに表示する例: {i: i for i in df.columns}。異なる列名をツールチップに表示する例: {'Rep': 'Republican', 'Dem': 'Democrat'}。テーブルに複数のヘッダー行がある場合、`tooltip_header`アイテムの値としてリストを使用します。tooltip*headerは次の型を持ちます: Dict with Strings as keys and values of type String | 要素を含むリスト delay, duration, type, value   - `delay` (optional): `delay`は、セルにホバーしたときにツールチップが表示されるまでの遅延をミリ秒単位で表します。これはテーブルの`tooltip*delay`プロパティを上書きします。`None`に設定すると、ツールチップは即座に表示されます。   -`duration`(optional):`duration`は、セルにホバーしたときにツールチップが表示される期間をミリ秒単位で表します。これはテーブルの`tooltip_duration`プロパティを上書きします。`None`に設定すると、ツールチップは消えません。代わりに、プロパティの値はプレーンな文字列でも構いません。この場合、`text`構文が使用されます。   -`type`('text', 'markdown'; optional): 各ツールチップ設定に対して、`type`はツールチップ生成に使用されるツールチップ構文のタイプを指します。`markdown`または`text`のいずれかです。デフォルトは`text`です。   -`value`(String; required):`value`は、構文ベースのツールチップの内容を指します。この値は必須です。 | Array of null | String | 要素を含むリスト delay, duration, type, value   -`delay`(optional)   -`duration`(optional)   -`type`('text', 'markdown'; optional)   -`value` (String; required)s
  * `virtualization` (Bool; optional): このプロパティは、レンダリング時にテーブルが仮想化を使用することを指示します。

仮定は次のとおりです: 列の幅は固定されている; 行の高さは常に同じ; ランタイムスタイルの変更は、最初のレンダリングに対する幅と高さに影響を与えません。
