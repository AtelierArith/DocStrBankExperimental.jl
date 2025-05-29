```
moonpos(jd[, radians=true]) -> ra, dec, dis, geolong, geolat
```

### 目的

指定されたユリウス日付における月の赤経と赤緯を計算します。

### 引数

  * `jd`: ユリウスエフェメリス日付。スカラーまたは配列のいずれかであることができます。
  * `radians`（オプションのブールキーワード）：`true`に設定されている場合、すべての出力角度量は度ではなくラジアンで与えられます。デフォルトは`false`です。

### 出力

5タプル `(ra, dec, dis, geolong, geolat)`：

  * `ra`: 指定された日付の真の赤道に対する月の見かけの赤経（度）
  * `dec`: 月の赤緯（度）
  * `dis`: 地球の中心と月の中心との距離（キロメートル）
  * `geolong`: 指定された日付の黄道に対する月の見かけの経度（度）
  * `geolat`: 指定された日付の黄道に対する月の見かけの緯度（度）

`jd`が配列の場合、すべての出力量は`jd`と同じ長さの配列になります。

### 方法

Chapront ELP2000/82月理論（Chapront-Touze'とChapront、1983、124、50）に基づいており、ジャン・ミューが``Astronomical Algorithms''（Willmann-Bell、Richmond）第2版、1998年の第47章で説明しています。ミューは経度で約10"、緯度で4"の精度を引用していますが、この精度の時間範囲は示していません。

IDL手続きと``Astronomical Algorithms''の例を比較すると、距離計算において非常に小さな不一致（約1 km）が見られますが、位置計算には違いはありません。

### 例

  * 1992年4月12日の月の位置を求める

    ```jldoctest
    julia> using AstroLib

    julia> jd = jdcnv(1992, 4, 12);

    julia> adstring(moonpos(jd)[1:2],precision=1)
    " 08 58 45.23  +13 46 06.1"
    ```

    これは天文年鑑に示された位置から1"以内です。
  * 2016年の地球と月の距離を6時間ごとにサンプリングしてプロットします。プロットには[Plots.jl](https://github.com/JuliaPlots/Plots.jl/)を使用します。

    ```julia
    using Dates
    using Plots
    points = DateTime(2016):Dates.Hour(6):DateTime(2017);
    plot(points, moonpos(jdcnv.(points))[3])
    ```

### 注意事項

この関数のコードはIDL天文学ユーザーライブラリに基づいています。
