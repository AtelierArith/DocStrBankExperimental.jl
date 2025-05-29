```
PlotConfig(;kwargs...)
```

プロットがレンダリングされる方法の側面を制御するためにフロントエンドに送信される構成オプション。受け入れ可能なキーワード引数は次のとおりです。

  * `scrollZoom`: マウスホイールまたは2本指のスクロールズームが有効かどうかを決定します。gl3d、geo、およびmapboxサブプロットではデフォルトでオンになっています（これらのサブプロットタイプにはパンによるズームボックスがないため）が、デフォルトでは直交サブプロットではオフになっています。すべてのサブプロットのスクロールを無効にするには、`scrollZoom`を*false*に設定します。
  * `editable`: グラフが編集可能かどうかを決定します。個別の部分をオーバーライドする別の`edits`構成項目がない限り、`edits`のすべての部分を設定します。
  * `staticPlot`: グラフがインタラクティブかどうかを決定します。*false*の場合、インタラクティビティはなく、エクスポートまたは画像生成用です。
  * `toImageButtonOptions`: toImageモードバーのボタンのオプションを静的にオーバーライドします。許可されるキーはformat、filename、width、heightです。
  * `displayModeBar`: モードバーの表示モードを決定します。*true*の場合、モードバーは常に表示されます。*false*の場合、モードバーは常に非表示です。*hover*の場合、モードバーはマウスカーソルがグラフコンテナ上にあるときに表示されます。
  * `modeBarButtonsToRemove`: 名前でモードバーのボタンを削除します。
  * `modeBarButtonsToAdd`: 構成オブジェクトを使用してモードバーのボタンを追加します。事前定義されたモードバーのボタン（例：形状描画、ホバー、スパイクライン）を有効にするには、それらの文字列名を提供するだけです。これには次のものが含まれる場合があります：*v1hovermode*、*hoverclosest*、*hovercompare*、*togglehover*、*togglespikelines*、*drawline*、*drawopenpath*、*drawclosedpath*、*drawcircle*、*drawrect*および*eraseshape*。これらの事前定義されたボタンは、グラフで使用されるすべてのトレースタイプと互換性がある場合にのみ表示されることに注意してください。
  * `modeBarButtons`: 外側の配列がボタングループを表し、内側の配列がボタンの構成オブジェクトまたはデフォルトボタンの名前を持つネストされた配列として、完全にカスタムのモードバーのボタンを定義します。
  * `showLink`: 結果のグラフの右下隅にChart Studio Cloudへのリンクが表示されるかどうかを決定します。`sendData`および`linkText`と一緒に使用します。
  * `plotlyServerURL`: 設定されると、'Edit in Chart Studio' `showEditInChartStudio`/`showSendToCloud`モードバーのボタンと、グラフ上のshowLink/sendDataリンクのベースURLを決定します。データをChart Studio Cloudに送信するには、`plotlyServerURL`を'https://chart-studio.plotly.com'に設定し、`showSendToCloud`をtrueに設定する必要があります。
  * `linkText`: `showLink`リンクに表示されるテキストを設定します。
  * `showEditInChartStudio`: `showSendToCloud`と同じですが、フロッピーディスクの代わりに鉛筆アイコンを使用します。`showSendToCloud`と`showEditInChartStudio`の両方がオンになっている場合、`showEditInChartStudio`のみが尊重されることに注意してください。
  * `locale`: どのローカリゼーションを使用すべきですか？ 'en'または'en-US'のような文字列である必要があります。
  * `displaylogo`: プロットのモードバーの端にplotlyロゴが表示されるかどうかを決定します。
  * `responsive`: ウィンドウがリサイズされたときにレイアウトサイズを変更するかどうかを決定します。
  * `doubleClickDelay`: ダブルクリックを登録するための遅延をms単位で設定します。これは、ダブルクリックを構成するための最初のマウスダウンと2回目のマウスアップの間の時間間隔（ms単位）です。この設定は、すべてのサブプロットのダブルクリック（geoおよびmapboxを除く）およびレジェンドのダブルクリックに伝播します。
