```
struct TLE
```

TLE（2行要素）の要素を同じ単位で格納します。

!!! note
    TLE文字列を作成または解析する際にのみ必要な行のチェックサムのフィールドはありません。


# フィールド

  * `name`: 衛星の名前。

## 最初の行

  * `satellite_number`: 衛星番号。
  * `classification`: 分類（'U'、'C'、または'S'）。
  * `international_designator`: 国際識別子。
  * `epoch_year`: エポック年（2桁）。
  * `epoch_day`: エポック日（日 + 日の小数部）。
  * `dn_o2`: 平均運動の1回目の時間微分 / 2 [rev/day²]。
  * `ddn_o6`: 平均運動の2回目の時間微分 / 6 [rev/day³]。
  * `bstar`: B*抗力項。
  * `element_set_number`: 要素セット番号。

## 2行目

  * `incliantion`: 傾斜 [deg]。
  * `raan`: 昇交点の右昇交点 [deg]。
  * `eccentricity`: 離心率 [ ]。
  * `argument_of_perigee`: 近点引数 [deg]。
  * `mean_anomaly`: 平均異常 [deg]。
  * `mean_motion`: 平均運動 [rev/day]。
  * `revolution_number`: エポック時の周回数 [rev]。

# TLEの作成

`TLE(; kwargs...)`関数を呼び出すことで手動で`TLE`を作成できます。ここで、`kwargs...`はフィールドと同じ名前のキーワード引数です。この場合、次の要素が必要です：

  * `epoch_year`、`epoch_day`、`inclination`、`raan`、`eccentricity`、`argument_of_perigee`、`mean_anomaly`および`mean_motion`。

他のものはオプションであり、存在しない場合はデフォルト値が割り当てられます。
