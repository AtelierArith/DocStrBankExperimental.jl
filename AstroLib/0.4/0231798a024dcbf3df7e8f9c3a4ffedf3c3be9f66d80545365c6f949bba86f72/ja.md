```
nutate(jd) -> long, obliq
```

### 目的

与えられたユリウス日付に対する経度と傾斜の摂動を返します。

### 引数

  * `jd`: ユリウスエフェメリス日付、スカラーまたはベクトルのいずれかです。

### 出力

2タプル `(long, obliq)`、ここで

  * `long`: 経度の摂動
  * `obl`: 緯度の摂動

`jd` が配列の場合、`long` と `obl` は同じ長さの配列です。

### 方法

ジャン・メウスの「天文アルゴリズム」第22章の公式を使用しています（1998年、2版）。これは1980年のIAU摂動理論に基づいており、0.0003"より大きいすべての項を含みます。

### 例

  * 1987年4月10日0時の経度と傾斜の摂動を求めます。これはメウスの例22.aです。

    ```jldoctest
    julia> using AstroLib

    julia> jd = jdcnv(1987, 4, 10);

    julia> nutate(jd)
    (-3.787931077110494, 9.44252069864449)
    ```
  * 21世紀の間の経度と傾斜の摂動を日ごとにプロットします。プロットには [Plots.jl](https://github.com/JuliaPlots/Plots.jl/) を使用します。

    ```julia
    using Dates
    using Plots
    years = DateTime(2000):DateTime(2100);
    long, obl = nutate(jdcnv.(years));
    plot(years, long); plot(years, obl)
    ```

摂動の支配的な大規模周期18.6年と、より短い周期の小さな振動の両方を見ることができます。

### 注意事項

この関数のコードはIDL天文学ユーザーライブラリに基づいています。
