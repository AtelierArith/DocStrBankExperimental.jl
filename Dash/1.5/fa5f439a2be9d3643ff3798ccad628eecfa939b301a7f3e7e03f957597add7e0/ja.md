```
dcc_datepickersingle(;kwargs...)
```

DatePickerSingleコンポーネントDatePickerSingleは、カレンダーから1日を選択するために特別に設計されたコンポーネントです。

DatePickerは、Pythonのdatetimeモジュールとよく統合されており、startDateとendDateはdatetimeオブジェクトを作成するのに適した文字列形式で返されます。

このコンポーネントは、こちらで見つけることができるAirbnbのreact-datesのreactコンポーネントに基づいています: https://github.com/airbnb/react-dates

  * `id` (String; optional): このコンポーネントのIDで、コールバック内でダッシュコンポーネントを識別するために使用されます。

IDはアプリ内のすべてのコンポーネントで一意である必要があります。

  * `calendar_orientation` ('vertical', 'horizontal'; optional): カレンダーの向き、垂直または水平のいずれか。

有効なオプションは「vertical」または「horizontal」です。

  * `className` (String; optional): ラッパーdivコンポーネントにCSSクラスを追加します。
  * `clearable` (Bool; optional): ドロップダウンが「クリア可能」であるかどうか、つまり、

選択された値を削除する小さな「x」がドロップダウンの右側に表示されるかどうか。

  * `date` (String; optional): コンポーネントの開始日を指定します。最良のプラクティスは、

datetimeオブジェクトを介して値を渡すことです。

  * `day_size` (optional): 描画されたカレンダーの日のサイズ、高い数値は

日サイズが大きく、全体的に大きなカレンダーを意味します。

  * `disabled` (Bool; optional): Trueの場合、日付を選択できません。
  * `disabled_days` (Array of Strings; optional): min*date*allowedとmax*date*allowedの間で

無効にすべき追加の日を指定します。受け入れられるdatetime.datetimeオブジェクトまたは'YYYY-MM-DD'形式の文字列。

  * `display_format` (String; optional): 選択された日付が表示される形式を指定します。

有効な形式は「MM YY DD」のバリエーションです。例えば：「MM YY DD」は1997年5月10日に対して'05 10 97'として表示され、「MMMM, YY」は1997年5月10日に対して'May, 1997'として表示され、「M, D, YYYY」は1997年9月10日に対して'07, 10, 1997'として表示され、「MMMM」は1997年5月10日に対して'May'として表示されます。

  * `first_day_of_week` (0, 1, 2, 3, 4, 5, 6; optional): 週の最初の日を指定します。値は

[0, ..., 6]の範囲で、0は日曜日、6は土曜日を示します。

  * `initial_visible_month` (String; optional): ユーザーがカレンダーを開いたときに最初に表示される月を指定します。datetime.datetimeオブジェクトまたは'YYYY-MM-DD'形式の文字列を受け入れます。
  * `is_RTL` (Bool; optional): カレンダーと日が左から右に動作するか、右から左に動作するかを決定します。
  * `loading_state` (要素を含むリストはis*loading、prop*name、component*name - `is*loading`(Bool; optional): コンポーネントが読み込まれているかどうかを決定します -`prop*name`(String; optional): どのプロパティが読み込まれているかを保持します -`component*name` (String; optional): 読み込まれているコンポーネントの名前を保持します; optional): dash-rendererからの読み込み状態オブジェクトを保持するオブジェクト。
  * `max_date_allowed` (String; optional): コンポーネントで選択可能な最も高い日付を指定します。

datetime.datetimeオブジェクトまたは'YYYY-MM-DD'形式の文字列を受け入れます。

  * `min_date_allowed` (String; optional): コンポーネントで選択可能な最も低い日付を指定します。

datetime.datetimeオブジェクトまたは'YYYY-MM-DD'形式の文字列を受け入れます。

  * `month_format` (String; optional): カレンダーで表示される月の形式を指定します。

有効な形式は「MM YY」のバリエーションです。例えば：「MM YY」は1997年5月に対して'05 97'として表示され、「MMMM, YYYY」は1997年5月に対して'May, 1997'として表示され、「MMM, YY」は1997年9月に対して'Sep, 97'として表示されます。

  * `number_of_months_shown` (optional): カレンダーが開かれたときに表示されるカレンダーの月の数。
  * `persisted_props` (Array of 'date's; optional): ユーザーの操作がコンポーネントまたはページをリフレッシュした後も持続するプロパティ。通常、このプロパティは無視できます。
  * `persistence` (Bool | String; optional): このコンポーネントでのユーザーの操作を持続させるために使用されます。

コンポーネントまたはページがリフレッシュされたときに。`persisted`が真であり、以前の値から変更されていない場合、ユーザーがアプリを使用している間に変更した`date`は、その変更を保持します。新しい`date`が元々与えられたものと一致する限り。`persistence_type`と組み合わせて使用されます。

  * `persistence_type` ('local', 'session', 'memory'; optional): 持続されたユーザーの変更が保存される場所：

memory: メモリ内にのみ保持され、ページリフレッシュ時にリセットされます。local: window.localStorage、データはブラウザを終了した後も保持されます。session: window.sessionStorage、データはブラウザを終了するとクリアされます。

  * `placeholder` (String; optional): 日付が選択されていないときに日付ピッカーの入力ボックスに表示されるテキスト。デフォルト値は'Start Date'です。
  * `reopen_calendar_on_clear` (Bool; optional): Trueの場合、クリアされたときにカレンダーが自動的に開きます。
  * `show_outside_days` (Bool; optional): Trueの場合、カレンダーは次の月に繰り越される日を表示します。
  * `stay_open_on_select` (Bool; optional): Trueの場合、ユーザーが値を選択したときにカレンダーは閉じず、ユーザーがカレンダーの外をクリックするまで待機します。
  * `style` (Dict; optional): ラッパーdivに追加されるCSSスタイル。
  * `with_full_screen_portal` (Bool; optional): Trueの場合、カレンダーはフルスクリーンのオーバーレイポータルで開きます。両方がTrueに設定されている場合は'withPortal'よりも優先されます。垂直カレンダーではサポートされていません。
  * `with_portal` (Bool; optional): Trueの場合、カレンダーは画面オーバーレイポータルで開きます。

垂直カレンダーではサポートされていません。
