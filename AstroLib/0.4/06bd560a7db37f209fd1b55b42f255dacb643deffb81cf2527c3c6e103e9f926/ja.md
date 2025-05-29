```
zenpos(jd, latitude, longitude) -> zenith_right_ascension, declination
zenpos(date, latitude, longitude, tz) -> zenith_right_ascension, declination
```

### 目的

与えられたユリウス日またはローカル市民時間とタイムゾーンに対して、天頂の赤経と declination をラジアンで返します。

### 説明

ローカル恒星時は、[`ct2lst`](@ref) の助けを借りて計算され、これは天頂の赤経です。これと観測所の緯度（declination に対応する）はラジアンに変換され、天頂方向として返されます。

### 引数

この関数は2つの異なる方法で呼び出すことができます。両方の方法に共通する引数は `latitude` と `longitude` です：

  * `latitude` : 希望する場所の緯度。
  * `longitude` : 希望する場所の経度。

天頂方向は、ユリウス日を提供することによって計算できます：

  * `jd` : 天頂位置が必要な日付と時間のユリウス日。

または、タイムゾーンと日付を提供することによって：

  * `tz`: 希望する場所のタイムゾーン（時間単位）（例：4 = EDT, 5 = EST）
  * `date`: `DateTime` 型のローカル市民時間。

### 出力

2つのタプル `(ra, dec)`：

  * `ra` : 天頂の赤経（ラジアン）。
  * `dec` : 天頂の declination（ラジアン）。

### 例

```jldoctest
julia> using AstroLib, Dates

julia> zenpos(DateTime(2017, 04, 25, 18, 59), 43.16, -24.32, 4)
(0.946790432684706, 0.7532841051607526)

julia> zenpos(jdcnv(2016, 05, 05, 13, 41), ten(35,0,42), ten(135,46,6))
(3.5757821152779536, 0.6110688599440813)
```

### 注意

この関数のコードは IDL Astronomy User's Library に基づいています。
