星独立の天文学パラメータにおいて、呼び出し元によって明示的に提供された地球回転角のみを更新します。

この関数は国際天文学連合のSOFA（基礎天文学の標準）ソフトウェアコレクションの一部です。

ステータス: サポート関数。

与えられた:    theta   double      地球回転角（ラジアン、注2）    astrom  iauASTROM*  星独立の天文学パラメータ:       pmt    double       使用されていない       eb     double[3]    使用されていない       eh     double[3]    使用されていない       em     double       使用されていない       v      double[3]    使用されていない       bm1    double       使用されていない       bpn    double[3][3] 使用されていない       along  double       経度 + s'（ラジアン）       xpl    double       使用されていない       ypl    double       使用されていない       sphi   double       使用されていない       cphi   double       使用されていない       diurab double       使用されていない       eral   double       使用されていない       refa   double       使用されていない       refb   double       使用されていない

返される:    astrom  iauASTROM*  星独立の天文学パラメータ:       pmt    double       変更なし       eb     double[3]    変更なし       eh     double[3]    変更なし       em     double       変更なし       v      double[3]    変更なし       bm1    double       変更なし       bpn    double[3][3] 変更なし       along  double       変更なし       xpl    double       変更なし       ypl    double       変更なし       sphi   double       変更なし       cphi   double       変更なし       diurab double       変更なし       eral   double       "ローカル" 地球回転角（ラジアン）       refa   double       変更なし       refb   double       変更なし

ノート:

1. この関数は、恒星追跡アプリケーションが天文学パラメータの大部分の無駄な再計算を回避できるようにするために存在します: 地球回転のみが更新されます。
2. 春分点に基づく位置として表現されたターゲット、例えば古典的な地心の見かけの（RA,Dec）に対して、提供されたthetaは地球回転角ではなくグリニッジの見かけの恒星時である可能性があります。
3. 関数iauAper13は、現在の関数の代わりに使用でき、ERA自体ではなくUT1から始まります。
4. これは、天文学的変換のチェーンに必要な星独立のパラメータをastrom構造に挿入するいくつかの関数の1つです: ICRS <-> GCRS <-> CIRS <-> 観測。

さまざまな関数は、異なる観測者のクラスと変換チェーンの部分をサポートします:

```
     関数             観測者        変換

  iauApcg iauApcg13    地心          ICRS <-> GCRS
  iauApci iauApci13    地上          ICRS <-> CIRS
  iauApco iauApco13    地上          ICRS <-> 観測
  iauApcs iauApcs13    宇宙          ICRS <-> GCRS
  iauAper iauAper13    地上          地球回転を更新
  iauApio iauApio13    地上          CIRS <-> 観測
```

"13"で終わる名前のものは、さまざまな天体暦を計算するために現代のSOFAモデルを使用します。他のものは呼び出し元によって提供された天体暦を受け入れます。

ICRSからGCRSへの変換は、空間運動、視差、光の屈折、及びアバレーションをカバーします。GCRSからCIRSへの変換は、フレームバイアスと歳差- nutationを含みます。CIRSから観測への変換は、地球回転、極運動、日周アバレーション、及び視差を考慮します（ICRS <-> GCRS変換に組み込まれていない限り）、及び大気屈折を考慮します。

この改訂:   2013年9月25日

SOFAリリース 2018-01-30

著作権 (C) 2018 IAU SOFA委員会。 末尾のノートを参照してください。
