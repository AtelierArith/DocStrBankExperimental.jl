自然方向を適切な方向に変換するために、アバレーションを適用します。

この関数は、国際天文学連合のSOFA（基礎天文学の標準）ソフトウェアコレクションの一部です。

ステータス: サポート関数。

与えられた:    pnat    double[3]   ソースへの自然方向（単位ベクトル）    v       double[3]   観測者のバリセントリック速度（c単位）    s       double      太陽と観測者の間の距離（au）    bm1     double      sqrt(1-|v|^2): ローレンツ因子の逆数

返される:    ppr     double[3]   ソースへの適切な方向（単位ベクトル）

注意:

1. アルゴリズムは、説明補足（Urban & Seidelmann 2013）の式（7.40）に基づいていますが、以下の変更が加えられています:       - 厳密な正規化が適用され、近似的な正規化は行われません。       - Klioner（2003）の式（7）からの重力ポテンシャル項が追加され、太陽の寄与のみを考慮しています。  これにより、最大で約0.4マイクロアーク秒の影響があります。
2. ほとんどすべてのケースにおいて、最大の精度は提供された速度によって制限されます。  たとえば、SOFAのiauEpv00関数が使用される場合、最大で5マイクロアーク秒の誤差が発生する可能性があります。

参考文献:

  * Urban, S. & Seidelmann, P. K. (eds), Explanatory Supplement to

the Astronomical Almanac, 3rd ed., University Science Books    (2013).

  * Klioner, Sergei A., "A practical relativistic model for micro-

arcsecond astrometry in space", Astr. J. 125, 1580-1597 (2003).

呼び出し:    iauPdp       2つのpベクトルのスカラー積

この改訂:   2013年10月9日

SOFAリリース 2018-01-30

著作権 (C) 2018 IAU SOFA Board.  最後にノートを参照してください。
