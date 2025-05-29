```
sat_tracks(; geocentric::Bool=false, tiles::Bool=false, position::Bool=false, kwargs...)
```

TLE（Two Line Elementsセット）を使用して衛星の軌道を計算します。これは、地球を周回する物体の特定の時点での軌道に関する情報を含むデータ形式です。また、AQUAおよびTERRA衛星のシーンの範囲を囲むポリゴンを計算し、シーン名を作成することもできます。これにより、そのデータを直接ダウンロードする手段が提供されます。

  * `start`: `DateTime(start)`でDateTimeに変換可能な文字列またはDateTimeオブジェクトで、軌道計算の開始時刻を指定します。省略した場合、UTCの現在時刻が使用されます。
  * `duration`: 軌道が計算される時間の長さ。日、時間、分、または秒での期間を受け入れます。デフォルトは分（100分）です。他の単位を使用するには、値に'D'、'h'、'm'、または's'を追加した文字列を使用します。*例* `duration="55m"`は、`start`から55分の軌道を計算します。
  * `step`または`inc`または`dt`: 軌道に沿った位置を計算する時間間隔。ここでのデフォルト単位は秒（30秒）ですが、'm'を追加することで分も使用できます。*例* `step="1m"`
  * `stop`: `duration`の代わりに軌道の終了日を提供します。`start`と同じ条件です。
  * `position`: `start`時刻での最初の位置のみを計算します。ブール値で、`position=true`を使用します。
  * `geocentric`: 出力が`lon,lat,alt,time`（デフォルト）または`ECEF`座標+時間かを制御するブール値です。
  * `tle`または`TLE`: 特定の衛星と期間のTLEデータを含むファイル名。TLEファイルの最初と2行目の2要素の文字列ベクターでも構いません。
  * `tiles`: 一部の衛星のシーンの制限とファイル名を計算します。現在はAQUAのみです。
  * `sat`、`SAT`または`satellite`: 使用する衛星の名前。選択肢は（文字列またはシンボル）:TERRA、:AQUAです。`tiles`オプションと一緒にのみ使用します。

### 戻り値

軌道またはシーンポリゴンを含むGMTdataset

## 例:

現在のローカル時間から始まるAQUA衛星の軌道を1つ計算します。これは2021年9月の月に対して正確です。他の日付には更新されたTLEが必要です。

```
tle1 = "1 27424U 02022A   21245.83760660  .00000135  00000-0  39999-4 0  9997";
tle2 = "2 27424  98.2123 186.0654 0002229  67.6025 313.3829 14.57107527 28342";
orb = sat_tracks(tle=[tle1; tle2], duration=100);
```

そして、軌道トラックは次のように視覚化できます。

```
imshow(orb,  proj=:Robinson, region=:global, coast=true)
```

WARNING: この関数はデフォルトでロードされていないSatelliteToolbox拡張に依存しています。次のコマンドでロードしてください：

  * $$
    using RemoteS, SatelliteToolboxTle, SatelliteToolboxPropagators, SatelliteToolboxTransformations
    $$
