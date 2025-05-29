```
dcc_graph(;kwargs...)
```

GraphコンポーネントGraphは、任意のplotly.jsを使用したデータビジュアライゼーションをレンダリングするために使用できます。

ユーザーのGraphとのインタラクションに基づいてコールバックを定義できます。たとえば、ホバー、クリック、または選択などです。

  * `id` (String; optional): このコンポーネントのIDで、コールバック内でダッシュコンポーネントを識別するために使用されます。このIDは、アプリ内のすべてのコンポーネントで一意である必要があります。
  * `animate` (Bool; optional): ベータ版: trueの場合、plotly.jsの`animate`関数を使用して更新間でアニメーションします。
  * `animation_options` (Dict; optional): ベータ版: アニメーション設定を含むオブジェクト。`animate`が`true`の場合にのみ適用されます。
  * `className` (String; optional): 親divのclassName
  * `clear_on_unhover` (Bool; optional): Trueの場合、ユーザーがポイントから「ホバー解除」したときに`hoverData`プロパティをクリアします。Falseの場合、`hoverData`プロパティは最後にホバーしたポイントのデータと等しくなります。
  * `clickAnnotationData` (Dict; optional): 最新のクリックアノテーションイベントからのデータ。読み取り専用。
  * `clickData` (Dict; optional): 最新のクリックイベントからのデータ。読み取り専用。
  * `config` (optional): Plotly.jsの設定オプション。

詳細については、https://plotly.com/javascript/configuration-options/を参照してください。configは次の型を持ちます: staticPlot、plotlyServerURL、editable、editSelection、edits、autosizable、responsive、queueLength、fillFrame、frameMargins、scrollZoom、doubleClick、doubleClickDelay、showTips、showAxisDragHandles、showAxisRangeEntryBoxes、showLink、sendData、linkText、displayModeBar、showSendToCloud、showEditInChartStudio、modeBarButtonsToRemove、modeBarButtonsToAdd、modeBarButtons、toImageButtonOptions、displaylogo、watermark、plotGlPixelRatio、topojsonURL、mapboxAccessToken、locale、localesを含むリスト   - `staticPlot` (Bool; optional): インタラクティビティなし、エクスポートまたは画像生成用   - `plotlyServerURL` (String; optional): `showSendToCloud`が有効な場合のPlotlyクラウドインスタンスのベースURL   - `editable` (Bool; optional): タイトルの編集、アノテーションの移動などが可能 - 別の`edits`設定項目が個々の部分を上書きしない限り、すべての`edits`の部分を設定します   - `editSelection` (Bool; optional): 選択の移動を有効にします   - `edits` (optional): 編集可能なプロパティのセット。editsは次の型を持ちます: annotationPosition、annotationTail、annotationText、axisTitleText、colorbarPosition、colorbarTitleText、legendPosition、legendText、shapePosition、titleTextを含むリスト   - `annotationPosition` (Bool; optional): アノテーションの主なアンカーで、テキスト（矢印がない場合）または矢印（全体をドラッグし、矢印の長さと方向は変更しない）   - `annotationTail` (Bool; optional): 矢印のあるアノテーション専用、矢印の長さと方向を変更   - `annotationText` (Bool; optional)   - `axisTitleText` (Bool; optional)   - `colorbarPosition` (Bool; optional)   - `colorbarTitleText` (Bool; optional)   - `legendPosition` (Bool; optional)   - `legendText` (Bool; optional): 凡例からトレース名フィールドを編集   - `shapePosition` (Bool; optional)   - `titleText` (Bool; optional): グローバル`layout.title`   - `autosizable` (Bool; optional): layout.autosizeに関係なく1回自動サイズを行う（それ以外はデフォルトの幅または高さの値を使用）   - `responsive` (Bool; optional): ウィンドウサイズが変更されたときにレイアウトサイズを変更するかどうか   - `queueLength` (optional): アンドゥ/リドゥキューの長さを設定   - `fillFrame` (Bool; optional): 自動サイズを行う場合、コンテナまたは画面を埋めますか？   - `frameMargins` (optional): 自動サイズを行う場合、プロットサイズのパーセントでフレームマージンを設定   - `scrollZoom` (Bool; optional): マウスホイールまたは2本指のスクロールでプロットをズーム   - `doubleClick` (false, 'reset', 'autosize', 'reset+autosize'; optional): ダブルクリックインタラクション（false、'reset'、'autosize'または'reset+autosize'）   - `doubleClickDelay` (optional): ダブルクリックイベントを登録するための遅延（ms）。最小値は100、最大値は1000です。デフォルトは300です。   - `showTips` (Bool; optional): 新しいユーザーにインタラクティビティに関するヒントを表示   - `showAxisDragHandles` (Bool; optional): 軸のパン/ズームドラッグハンドルを有効にします   - `showAxisRangeEntryBoxes` (Bool; optional): パン/ズームドラッグポイントでの直接範囲入力を有効にします（上記でドラッグハンドルを有効にする必要があります）   - `showLink` (Bool; optional): このプロットをplotlyで開くためのリンク   - `sendData` (Bool; optional): リンクを表示する場合、それはデータを含むか、単にplotlyファイルへのリンクですか？   - `linkText` (String; optional): sendDataリンクに表示されるテキスト   - `displayModeBar` (true, false, 'hover'; optional): モードバーを表示（true、false、または'hover'）   - `showSendToCloud` (Bool; optional): このデータをPlotly Cloudインスタンスに送信するためのモードバーのボタンを含めるべきかどうか。デフォルトではfalseです。   - `showEditInChartStudio` (Bool; optional): このデータをPlotly Chart Studioプロットに送信するためのモードバーのボタンを表示するべきかどうか。これとshowSendToCloudの両方が選択されている場合、showEditInChartStudioのみが尊重されます。デフォルトではfalseです。   - `modeBarButtonsToRemove` (Array; optional): 名前でモードバーのボタンを削除します。すべてのモードバーのボタン名は、https://github.com/plotly/plotly.js/blob/master/src/components/modebar/buttons.jsにあります。一般的な名前には、sendDataToCloud; (2D) zoom2d、pan2d、select2d、lasso2d、zoomIn2d、zoomOut2d、autoScale2d、resetScale2d; (Cartesian) hoverClosestCartesian、hoverCompareCartesian; (3D) zoom3d、pan3d、orbitRotation、tableRotation、handleDrag3d、resetCameraDefault3d、resetCameraLastSave3d、hoverClosest3d; (Geo) zoomInGeo、zoomOutGeo、resetGeo、hoverClosestGeo; hoverClosestGl2d、hoverClosestPie、toggleHover、resetViewsが含まれます。   - `modeBarButtonsToAdd` (Array; optional): 設定オブジェクトを使用してモードバーのボタンを追加します   - `modeBarButtons` (Bool | Real | String | Dict | Array; optional): ネストされた配列としての完全カスタムモードバーのボタンで、外側の配列はボタングループを表し、内側の配列にはボタンの設定オブジェクトまたはデフォルトボタンの名前があります   - `toImageButtonOptions` (optional): toImageモードバーのボタンの動作を変更します。toImageButtonOptionsは次の型を持ちます: format、filename、width、height、scaleを含むリスト   - `format` ('jpeg', 'png', 'webp', 'svg'; optional): 作成するファイル形式   - `filename` (String; optional): ダウンロードされるファイルに付けられる名前   - `width` (optional): ダウンロードされるファイルの幅（px）   - `height` (optional): ダウンロードされるファイルの高さ（px）   - `scale` (optional): 指定された幅と高さでレンダリングした後にファイルに与える追加の解像度   - `displaylogo` (Bool; optional): モードバーの端にplotlyロゴを追加します   - `watermark` (Bool; optional): モードバーがなくてもplotlyロゴを追加します   - `plotGlPixelRatio` (optional): Glプロット画像のピクセル比を増加させます   - `topojsonURL` (String; optional): 地理チャートで使用されるtopojsonファイルへのURL   - `mapboxAccessToken` (Bool | Real | String | Dict | Array; optional): Mapboxアクセス・トークン（mapboxトレースタイプをプロットするために必要）Mapbox Atlasサーバーを使用している場合、このオプションを''に設定して、plotly.jsがパブリックMapboxサーバーに認証を試みないようにします。   - `locale` (String; optional): 使用するロケール。ロケールはプロットと共に提供することも、ページ上で読み込むこともできます。詳細は、https://github.com/plotly/plotly.js/blob/master/dist/README.md#to-include-localizationを参照してください。   - `locales` (Dict; optional): ローカリゼーション定義。プロットと共に提供することを選択した場合、グローバルに登録するのではなく。

  * `extendData` (Array | Dict; optional): 既存のトレースに追加されるデータ。形式は

`[updateData, traceIndices, maxPoints]`で、`updateData`は拡張するデータを含むオブジェクト、`traceIndices`（オプション）は拡張するトレースインデックスの配列、`maxPoints`（オプション）は許可される最大ポイント数を定義する整数または`updateData`に一致するkey:valueペアを持つオブジェクトです。完全な使用法については、Plotly.extendTraces APIを参照してください: https://plotly.com/javascript/plotlyjs-function-reference/#plotlyextendtraces

  * `figure` (data、layout、framesを含むリスト   - `data` (Array of Dicts; optional)   - `layout` (Dict; optional)   - `frames` (Array of Dicts; optional); optional): Plotly `figure`オブジェクト。スキーマを参照してください:

https://plotly.com/javascript/reference

`config`は`config`プロパティによって別に設定されます。

  * `hoverData` (Dict; optional): 最新のホバーイベントからのデータ。読み取り専用。
  * `loading_state` (is*loading、prop*name、component*nameを含むリスト   - `is*loading`(Bool; optional): コンポーネントが読み込まれているかどうかを判断します   -`prop*name`(String; optional): どのプロパティが読み込まれているかを保持します   -`component*name` (String; optional): 読み込まれているコンポーネントの名前を保持します; optional): dash-rendererからの読み込み状態オブジェクトを保持するオブジェクト
  * `mathjax` (Bool; optional): trueの場合、mathjax v3 (tex-svg)をページに読み込み、グラフで使用します。
  * `prependData` (Array | Dict; optional): 既存のトレースに追加されるデータ。形式は

`[updateData, traceIndices, maxPoints]`で、`updateData`は追加するデータを含むオブジェクト、`traceIndices`（オプション）は追加するトレースインデックスの配列、`maxPoints`（オプション）は許可される最大ポイント数を定義する整数または`updateData`に一致するkey:valueペアを持つオブジェクトです。完全な使用法については、Plotly.prependTraces APIを参照してください: https://plotly.com/javascript/plotlyjs-function-reference/#plotlyprependtraces

  * `relayoutData` (Dict; optional): ユーザーがプロットをズームまたはパンしたとき、または他のレイアウトレベルの編集を行ったときに発生する最新のリレイアウトイベントからのデータ。形式は`{<attr string>: <value>}`で、行われた変更を説明します。読み取り専用。
  * `responsive` (true, false, 'auto'; optional): Trueの場合、Plotly.jsプロットはウィンドウのリサイズおよび親要素のリサイズイベントに完全に応答します。これは、`config.responsive`をTrueに上書きし、`figure.layout.autosize`をTrueに設定し、`figure.layout.height`と`figure.layout.width`を解除することで実現されます。Falseの場合、Plotly.jsプロットはウィンドウのリサイズおよび親要素のリサイズイベントに応答しません。これは、`config.responsive`をFalseに上書きし、`figure.layout.autosize`をFalseに設定することで実現されます。'auto'（デフォルト）の場合、GraphはPlotly.jsプロットが完全に応答可能（True）かどうかを`config.responsive`、`figure.layout.autosize`、`figure.layout.height`、`figure.layout.width`の値に基づいて判断します。これはGraphコンポーネントのレガシー動作です。

適切な寸法/スタイリングを`style`プロパティを通じて組み合わせる必要があります。

  * `restyleData` (Array; optional): ユーザーが凡例項目を切り替えたり、parcoordsの選択を変更したり、他のトレースレベルの編集を行ったときに発生する最新のリスタイルイベントからのデータ。形式は`[edits, indices]`で、`edits`は行われた変更を説明するオブジェクト`{<attr string>: <value>}`で、`indices`は編集されたトレースインデックスの配列です。読み取り専用。
  * `selectedData` (Dict; optional): 最新の選択イベントからのデータ。読み取り専用。
  * `style` (Dict; optional): プロットdivに対する一般的なスタイルのオーバーライド

```
