```
[D =] weather(lon=0.0, lat=0.0; city::String="", last=0, days=7, year::Int=0, starttime::Union{DateTime, String}="",
              endtime::Union{DateTime, String}="", variable="temperature_2m", dryrun=false, show=false, kw...)
```

[Open-Meteo](https://open-meteo.com/en/docs) APIから取得した天気データをプロットおよび/または取得します。詳細についてはサイトを参照してください。プロットするための多くの変数があり、あまり明白でない名前が付けられています。また、変数には*予報*と*アーカイブ*のバージョンがあります。この関数は変数名からそれを推測しようとします。変数名のリストはかなり広範であり、ここで完全には再現しませんが、気候学的理由から興味があるため、いわゆる$daily$変数をリストアップします。

  * `variable`: "temperature*2m*max", "temperature*2m*min", "apparent*temperature*max", "apparent*temperature*min", "precipitation*sum", "rain*sum", "snowfall*sum", "precipitation*hours", "sunshine*duration", "daylight*duration", "wind*speed*10m*max", "wind*gusts*10m*max", "wind*direction*10m*dominant", "shortwave*radiation*sum", "et0*fao_evapotranspiration"

この関数にインスパイアされた[WeatherReport.jl](https://github.com/vnegi10/WeatherReport.jl)プロジェクトにも感謝の意を表します。このプロジェクトははるかに小さく（約25 LOC）、GMT自体以外の依存関係はありません。

  * `lon`と`lat`: 明示的に位置の座標を提供します。提供されない場合、または`city`名がない場合は、IP位置サービスから現在の位置が使用されます（`whereami`関数のヘルプを参照）。
  * `city`: 使用される位置の名前です。都市名は通常問題ありませんが、失敗した場合は、名前を座標に変換するために使用される`geocoder()`関数のヘルプを参照してください。デフォルトはユーザーの現在の地理的位置を使用します。
  * `days`: 予報を求めるとき、これは予報する日数です。最大は16日です。デフォルトは7日です。
  * `starttime`: 指定された開始時刻以降のイベントに制限します。注意: すべての時間はISO8601日付/時刻形式またはDateTime型を使用します。デフォルトはNOW - 30日です。
  * `endtime`: 指定された終了時刻以前のイベントに制限します。`starttime`と同様の注意事項があります。デフォルトは現在の時間です。
  * `last`: 値が整数（*例* `last=90`）の場合、過去n日間のイベントを選択します。文字列の場合は、'w'（週）、'm'（月）、または'y'（年）で終わることを期待します。例: `last="2Y"`（期間コードは大文字小文字を区別しません）
  * `year`: 整数で、この年にデータのダウンロードを制限します。
  * `dryrun`: 要求されたデータのURLを印刷して返します。
  * `data`: デフォルトは地震マップを作成しますが、`data`オプションが使用される場合（何でも含む）、$GMTdataset$でデータを返します。
  * `figname`: **savefig** | **figname** | **name** :: [Type => Str]

    `figname=name.ext`で図を保存します。ここで`ext`は図の形式を選択します（例: figname="name.png"）
  * `show`: デフォルトでは、この関数は`GMTdataset`内のデータを返すだけですが、`show=true`の場合はプロットを表示します。`show=true`の場合でもデータを返すには`data=true`を使用します。

### 例

```julia
# あなたの位置の温度予報をプロットします。また、データテーブルも返します。
D = weather(data=true, show=true)
```

```julia
# 2023年のコペンハーゲンでの降雨をプロットします
weather(city="Copenhagen", year=2023, variable="rain_sum", show=true)
```
