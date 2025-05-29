sat*scenes(track, sat*name::String)

AQUAおよびTERRAシーンを区切るポリゴンを計算します。

  * `trac`: `sat_tracks`を使用して1分間隔で計算された軌道（重要）
  * `sat_name`: 衛星名。この時点ではAQUAとTERRAのみが許可されています。

ポリゴンとデータセット`header`フィールド内のシーン名を含むGMTdatasetベクターを返します。

# 例

`orb`が次のように取得されたと仮定します。

orb = sat_tracks(tle=[tle1; tle2], start=DateTime("2021-09-02T13:30:00"), 	stop=DateTime("2021-09-02T13:40:00"), step="1m");

シーンの境界（2つ）は次のように計算されます。

```
Dscenes = sat_scenes(orb, "AQUA");
```
