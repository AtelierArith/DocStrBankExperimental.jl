```
rhotheta(period, periastron, eccentricity, semimajor_axis, inclination, omega, omega2, epoch) -> rho, theta
```

### 目的

バイナリ星の分離と位置角を計算します。

### 説明

この関数は、軌道要素から導出された視覚的バイナリ星の分離 $ρ$ と位置角 $θ$ を返します。以下の書籍に記載されたアルゴリズムが使用されます：Meeus J., 1992, Astronomische Algorithmen, Barth。ページ400に示された例と比較して、相違は見つかりませんでした。

### 引数

  * `period`: 周期 [年]
  * `periastro`: 近日点通過の時刻 [年]
  * `eccentricity`: 軌道の離心率
  * `semimajor_axis`: 半長軸 [アーク秒]
  * `inclination`: 傾斜角 [度]
  * `omega`: ノード [度]
  * `omega2`: 近日点の経度 [度]
  * `epoch`: 観測のエポック [年]

すべての入力パラメータはスカラーでなければなりません。

### 出力

2タプル $(ρ, θ)$、ここで

  * $$
    ρ
    $$

    は分離 [アーク秒]、および
  * $$
    θ
    $$

    は位置角 [度] です。

### 例

エタ・コロナエ・ボレアリスの2016年のエポックでの位置を求めます。

```jldoctest
julia> using AstroLib

julia> ρ, θ = rhotheta(41.623, 1934.008, 0.2763, 0.907, 59.025, 23.717, 219.907, 2016)
(0.6351167848659552, 214.42513387396497)
```

### 注意

この関数のコードはIDL天文学ユーザーライブラリに基づいています。
