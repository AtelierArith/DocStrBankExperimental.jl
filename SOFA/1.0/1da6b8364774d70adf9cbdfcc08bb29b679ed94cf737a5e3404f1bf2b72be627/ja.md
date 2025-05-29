星独立天文学パラメータにおいて、地球回転角のみを更新します。呼び出し元はUT1を提供します（注：UTCではありません）。

この関数は国際天文学連合のSOFA（基礎天文学の標準）ソフトウェアコレクションの一部です。

ステータス：サポート関数。

与えられたもの： ut11    double      UT1の2部構成...    ut12    double      ...ユリウス日（注1）    astrom  iauASTROM*  星独立天文学パラメータ：    pmt    double       使用されていない    eb     double[3]    使用されていない    eh     double[3]    使用されていない    em     double       使用されていない    v      double[3]    使用されていない    bm1    double       使用されていない    bpn    double[3][3] 使用されていない    along  double       経度 + s'（ラジアン）    xpl    double       使用されていない    ypl    double       使用されていない    sphi   double       使用されていない    cphi   double       使用されていない    diurab double       使用されていない    eral   double       使用されていない    refa   double       使用されていない    refb   double       使用されていない

返されるもの： astrom  iauASTROM*  星独立天文学パラメータ：    pmt    double       変更なし    eb     double[3]    変更なし    eh     double[3]    変更なし    em     double       変更なし    v      double[3]    変更なし    bm1    double       変更なし    bpn    double[3][3] 変更なし    along  double       変更なし    xpl    double       変更なし    ypl    double       変更なし    sphi   double       変更なし    cphi   double       変更なし    diurab double       変更なし    eral   double       "ローカル" 地球回転角（ラジアン）    refa   double       変更なし    refb   double       変更なし

注：

1. UT1日（注：UTCではありません）ut11+ut12はユリウス日であり、引数ut11とut12の間で任意の便利な方法で配分されます。たとえば、JD(UT1)=2450123.7は、以下のように表現できます。

    `ut11           ut12`

    2450123.7           0.0       （JD方式）    2451545.0       -1421.3       （J2000方式）    2400000.5       50123.2       （MJD方式）    2450123.5           0.2       （日付と時間方式）

    JD方式は、いくつかの小数点以下の桁数の解像度の損失が許容される場合に最も自然で便利です。J2000およびMJD方式は、解像度と便利さの良い妥協です。日付と時間方式は、使用されるアルゴリズムに最も適合しています：ut11引数が問題の日の0時UT1のものであり、ut12引数が0から1の範囲にある場合、またはその逆の場合に最大の精度が提供されます。
2. 呼び出し元が地球回転角自体を提供したい場合は、代わりに関数iauAperを使用できます。この技術の1つの使用法は、グリニッジの見かけの恒星時を代入し、春分点に基づく変換を直接サポートすることです。
3. これは、天文学的変換のチェーンICRS <-> GCRS <-> CIRS <-> 観測に必要な星独立パラメータをastrom構造に挿入するいくつかの関数の1つです。

    様々な関数は、異なる観測者のクラスと変換チェーンの部分をサポートします：

    `関数             観測者        変換`

    iauApcg iauApcg13    地心      ICRS <-> GCRS    iauApci iauApci13    地上      ICRS <-> CIRS    iauApco iauApco13    地上      ICRS <-> 観測    iauApcs iauApcs13    宇宙      ICRS <-> GCRS    iauAper iauAper13    地上      地球回転を更新    iauApio iauApio13    地上      CIRS <-> 観測

    "13"で終わる名前のものは、現代のSOFAモデルを使用して様々な天体暦を計算します。他のものは、呼び出し元が提供する天体暦を受け入れます。

    ICRSからGCRSへの変換は、空間運動、視差、光の屈折、及びアバレーションをカバーします。GCRSからCIRSへの変換は、フレームバイアスと歳差- nutationを含みます。CIRSから観測への変換は、地球の回転、極運動、日周アバレーションおよび視差を考慮します（ICRS <-> GCRS変換に組み込まれていない限り）、および大気の屈折を考慮します。

呼び出し： iauAper      天文学パラメータ： ERAを更新    iauEra00     地球回転角、IAU 2000

この改訂：   2013年9月25日

SOFAリリース 2018-01-30

著作権 (C) 2018 IAU SOFA委員会。 末尾の注を参照してください。
