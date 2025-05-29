ICRSからCIRSへの迅速な変換、事前に計算された星独立の天文学パラメータを考慮し、視差と固有運動がゼロであると仮定します。

この関数の使用は、効率が重要であり、1つの日付に対して多くの星の位置を変換する必要がある場合に適しています。星独立のパラメータは、iauApci[13]、iauApcg[13]、iauApco[13]、またはiauApcs[13]のいずれかの関数を呼び出すことで取得できます。

非ゼロの視差と固有運動の場合の対応する関数はiauAtciqです。

この関数は、国際天文学連合のSOFA（基礎天文学の標準）ソフトウェアコレクションの一部です。

ステータス：サポート関数。

与えられたもの： rc,dc  double     ICRS天文学的RA,Dec（ラジアン）    astrom iauASTROM* 星独立の天文学パラメータ：       pmt    double       PM時間間隔（SSB、ユリウス年）       eb     double[3]    SSBから観測者へのベクトル（au）       eh     double[3]    太陽から観測者への単位ベクトル       em     double       太陽から観測者までの距離（au）       v      double[3]    重心観測者の速度（ベクトル、c）       bm1    double       sqrt(1-|v|^2)：ローレンツ因子の逆数       bpn    double[3][3] バイアス-歳差- nutation行列       along  double       経度 + s'（ラジアン）       xpl    double       地元の子午線に対する極運動xp（ラジアン）       ypl    double       地元の子午線に対する極運動yp（ラジアン）       sphi   double       測地的緯度の正弦       cphi   double       測地的緯度の余弦       diurab double       日周のアバレーションベクトルの大きさ       eral   double       "ローカル"地球回転角（ラジアン）       refa   double       屈折定数A（ラジアン）       refb   double       屈折定数B（ラジアン）

返されるもの：    ri,di  double     CIRS RA,Dec（ラジアン）

注意：

すべてのベクトルはBCRS軸に対してです。

参考文献：

Urban, S. & Seidelmann, P. K. (eds), Explanatory Supplement to    the Astronomical Almanac, 3rd ed., University Science Books    (2013).

Klioner, Sergei A., "A practical relativistic model for micro-    arcsecond astrometry in space", Astr. J. 125, 1580-1597 (2003).

呼び出し：    iauS2c       球面座標から単位ベクトルへの変換    iauLdsun     太陽による光の屈折    iauAb        星のアバレーション    iauRxp       r行列とpベクトルの積    iauC2s       pベクトルから球面への変換    iauAnp       角度を範囲+/- piに正規化

この改訂：   2013年10月9日

SOFAリリース2018-01-30

著作権 (C) 2018 IAU SOFA Board.  最後にノートを参照してください。
