```
ct2lst(longitude, jd) -> local_sidereal_time
ct2lst(longitude, tz, date) -> local_sidereal_time
```

### 目的

ローカル民間時間をローカル平均恒星時間に変換します。

### 引数

この関数は2つの異なる方法で呼び出すことができます。両方の方法に共通する唯一の引数は`longitude`です：

  * `longitude`: ローカル恒星時間を求める場所のグリニッジ東の経度（度）です。グリニッジ平均恒星時間（GMST）は、経度を`0`に設定することで求めることができます。

平均恒星時間に変換する民間日付は、ジュリアン日を提供することで指定できます：

  * `jd`: これは変換する日付のジュリアン日の数です。

または、タイムゾーンと日付を指定することもできます：

  * `tz`: グリニッジ子午線の東にあるサイトのタイムゾーン（時間）です（GMTよりも前）。このパラメータを使用して、夏時間を簡単に考慮できます（例：-4=EDT、-5=EST/CDT）。
  * `date`: これは`DateTime`型のローカル民間時間です。

### 出力

指定された日付/時間のローカル恒星時間（時間単位）。

### 方法

問題の日付と時間のジュリアン日を使用して、2000-01-01から経過した日数を求めます。これは、その日のGSTと組み合わせて、現在のGSTを外挿するために使用されます。これを使用してLSTを取得します。使用される定数については、Jean Meeusの『Astronomical Algorithms』のp. 84（Eq. 11-4）を参照してください。

### 例

2008年7月30日15時53分にメリーランド州ボルチモア（経度=-76.72度）でのグリニッジ平均恒星時間（GMST）を求めます。タイムゾーンはEDTまたはtz=-4です。

```jldoctest
julia> using AstroLib, Dates

julia> lst = ct2lst(-76.72, -4, DateTime(2008, 7, 30, 15, 53))
11.356505172312609

julia> sixty(lst)
3-element StaticArraysCore.SVector{3, Float64} with indices SOneTo(3):
 11.0
 21.0
 23.418620325392112
```

2015年11月24日13時21分にドイツのハイデルベルク（経度=08° 43' E）でのグリニッジ平均恒星時間（GMST）を求めます。タイムゾーンはCETまたはtz=1です。場所の経度とジュリアン日の数のみを使用して`ct2lst`を提供します。

```jldoctest
julia> using AstroLib, Dates

julia> longitude = ten(8, 43); # 経度を小数に変換します。

julia> # ジュリアン日の数を取得します。ローカル時間をUTCに変換するためにタイムゾーンを引くことを忘れないでください。

julia> jd = jdcnv(DateTime(2015, 11, 24, 13, 21) - Dates.Hour(1));

julia> lst = ct2lst(longitude, jd) # グリニッジ平均恒星時間を計算します。
17.140685171005316

julia> sixty(lst)
3-element StaticArraysCore.SVector{3, Float64} with indices SOneTo(3):
 17.0
  8.0
 26.466615619137883
```

### 注意事項

この関数のコードはIDL天文学ユーザーライブラリに基づいています。 ```
