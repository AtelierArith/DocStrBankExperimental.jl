ICRS星データを、エポックJ2000.0からCIRSに変換します。

この関数は、国際天文学連合のSOFA（基礎天文学の標準）ソフトウェアコレクションの一部です。

ステータス：サポート関数。

与えられたもの：     rc     double   J2000.0におけるICRSの赤経（ラジアン、注1）     dc     double   J2000.0におけるICRSの赤緯（ラジアン、注1）     pr     double   RAの固有運動（ラジアン/年；注2）     pd     double   Decの固有運動（ラジアン/年）     px     double   視差（アーク秒）     rv     double   放射速度（km/s、後退する場合は+ve）     date1  double   TDBを2部に分けた...     date2  double   ...ユリウス日（注3）

返されるもの：     ri,di  double*  CIRSの地心RA,Dec（ラジアン）     eo     double*  原点の方程式（ERA-GST、注5）

注：

```
1. J2000.0以外のエポックの星データ（例えば、エポックがJ1991.25のヒッパルコスカタログからのデータ）は、使用前にiauPmsafeを呼び出す必要があります。

2. RAの固有運動はdRA/dtであり、cos(Dec)*dRA/dtではありません。

3. TDB日付date1+date2はユリウス日であり、2つの引数の間で任意の便利な方法で分配されます。例えば、JD(TDB)=2450123.7は、以下のいずれかの方法で表現できます：

    date1          date2

    2450123.7           0.0       （JD法）
    2451545.0       -1421.3       （J2000法）
    2400000.5       50123.2       （MJD法）
    2450123.5           0.2       （日付と時間法）

JD法は、いくつかの小数点以下の桁数の解像度の損失が許容される場合に最も自然で便利です。J2000法は、引数が内部で処理される方法に最も適しており、最適な解像度を提供します。MJD法と日付と時間法は、解像度と便利さの間の良い妥協です。この関数のほとんどのアプリケーションでは、選択は全く重要ではありません。

TTは、精度に重大な影響を与えることなくTDBの代わりに使用できます。

4. 利用可能な精度は1ミリ秒角よりも良好であり、主に使用される歳差- nutationモデル（IAU 2000A/2006）によって制限されています。太陽系の天体に非常に近い場合、モデル化されていない光の屈折のために、数ミリ秒角までの追加の誤差が発生する可能性があります。ただし、太陽の寄与は、一次的に考慮されています。地球の位置と速度を計算するために使用されるSOFA関数iauEpv00の精度制限は、最大で5マイクロ秒角の誤差を引き起こす可能性があります。太陽の縁での光の屈折は、0.4ミリ秒角のレベルで不確かです。

5. (CIOベースの)中間地点ではなく、(等分点ベースの)見かけの位置への変換が必要な場合は、返された赤経から原点の方程式を引きます：RA = RI - EO。（必要に応じて、結果を従来の0-2π範囲に保つために、iauAnp関数を適用できます。）
```

呼び出し：     iauApci13    天文学パラメータ、ICRS-CIRS、2013     iauAtciq     ICRSからCIRSへのクイック変換

この改訂：   2017年3月12日

SOFAリリース2018-01-30

著作権 (C) 2018 IAU SOFA理事会。 末尾の注を参照してください。
