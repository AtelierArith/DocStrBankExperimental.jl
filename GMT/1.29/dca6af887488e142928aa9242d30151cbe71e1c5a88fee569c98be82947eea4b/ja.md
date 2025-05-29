```
seismicity(starttime="", endtime="", minmagnitude=3, mindepth=0, maxdepth=0, last=0, year=0, printurl=false, show=true, kw...)
```

USGS地震危険プログラムページから取得した世界中の地震活動の自動マップを作成します。 https://earthquake.usgs.gov

  * `starttime`: 指定された開始時刻以降のイベントに制限します。注意：すべての時間はISO8601日付/時刻形式またはDateTime型を使用します。デフォルトはNOW - 30日です。
  * `endtime`: 指定された終了時刻以前のイベントに制限します。`starttime`と同様の注意事項があります。デフォルトは現在の時刻です。
  * `minmagnitude`: 指定された最小値よりも大きいマグニチュードのイベントに制限します。
  * `mindepth`: 指定された最小値よりも深いイベントに制限します（kmは下向きに正）。
  * `maxdepth`: 指定された最大値よりも浅いイベントに制限します（kmは下向きに正）。
  * `last`: 値が整数の場合（*例* `last=90`）、過去n日間のイベントを選択します。文字列の場合は、'w'（週）、'm'（月）、または'y'（年）で終わることを期待します。例：`last="2Y"`（期間コードは大文字小文字を区別しません）
  * `year`: 整数で、この年にデータのダウンロードを制限します。
  * `printurl`: リクエストされたデータのURLを印刷します。
  * `circle`: $lon,lat,radius$の3要素のタプルまたは配列で、$radius$はkm単位で、円検索を実行します。
  * `data`: デフォルトは地震活動マップを作成しますが、`data`オプションが使用されると（何でも含む）$GMTdataset$でデータを返します。
  * `figname`: **savefig** | **figname** | **name** :: [Type => Str]

    `figname=name.ext`で図を保存します。ここで`ext`は図の形式を選択します（例：figname="name.png"）
  * `land`: デフォルトでは大陸を「バーレウッド」色で塗ります。$coast$モジュールのように、`land=`"othercolor"`を使用して置き換えます。
  * `layers`: デフォルトでは深さを3つの層に分けます；1-100、100-300および> 300 km。`layers=4`を使用して最上層を0-50および50-100 kmに細分化します。
  * `legend`: デフォルトでは凡例をプロットします。凡例コマンドの特定のオプション（例：`pos`、`box`など）は`kw...`オプションを介して渡されます。凡例を表示しないには`legend=false`を使用します。
  * `ocean`: デフォルトでは海を「ライトブルー」色で塗ります。`ocean=`"othercolor"`を使用して置き換えます。
  * `region`: 興味のある地域。デフォルトは[-180 180 -90 90]ですが、このオプションを受け入れる他のモジュールのようにサブリージョンを渡すことができます（例：$coast$）。
  * `proj`: デフォルトでは`region`の範囲に基づいて適切な投影を選択しますが、`proj=xxx`を指定することで上書きできます。例えば$coast$のように。
  * `size`: 同じサイズのすべてのイベントをプロットするためのスカラーです。このサイズはcm単位であることが期待されますが、> 1の場合はポイント単位として解釈されます。

      * `size=[min_sz max_sz]`は、最小/最大マグニチュードを線形にスケーリングしてサイズを`min_sz/max_sz`にします。
      * `size=([min_sz max_sz], [min_mag max_mag])`は、`min_mag/max_mag`マグニチュードを線形にスケーリングしてサイズを`min_sz/max_sz`にします。
      * `size=(fun, [min_sz max_sz] [, [min_mag max_mag]])`は、上記と同じことを行いますが、変換は関数'fun'によって決定されます。可能な関数は$exp10$、$exp$、$pow$および$sqrt$です。$pow$の場合は、指数も渡す必要があり、構文は次のようになります：`size=((pow,2), [min_sz max_sz])`で平方スケーリングを行います。
  * `show`: デフォルトではこの関数はプロットを表示します（`data`オプションがない場合）。表示を防ぐには`show=false`を使用します（そして、後続のコマンドからのプロットを受け入れるために図を開いたままにします）。

### 例

```julia
    seismicity(size=8)
    seismicity(marker=:star, size=[3 10])
    seismicity(size=(exp10, [2 12], [3 9]))
```
