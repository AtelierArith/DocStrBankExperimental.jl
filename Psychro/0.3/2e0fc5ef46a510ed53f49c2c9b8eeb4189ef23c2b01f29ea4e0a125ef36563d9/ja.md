湿った空気をモデル化するために使用される型

これは、ASHRAEハンドブックの心理測定法：理論と実践に記載されている定式を使用しています、参照 [5]。

温度範囲は `173.15 < T < 474.15 K` で、圧力は `P < 5 MPa` です。

このタイプを扱うメソッドは、実際の湿った空気のいくつかの熱力学を計算するために、参照 [1-2] の方程式を実装しています。

いくつかの熱力学的特性はメソッドとして実装されています。すべてのメソッドは、最初の引数として `MoistAir` 型、2 番目の引数として温度、湿度が指定される方法を宣言する型、使用する湿度の値、および圧力を引数として取ります。`Unitful` パッケージが使用されている場合、任意の単位を使用できます。一方、単位が提供されていない場合、パッケージはすべて SI 単位を仮定します。特に：

  * 温度は K
  * 圧力は Pa
  * 長さは m
  * 物質量は mol
  * 質量は kg
  * エネルギーは J

湿度を指定するために、次の型が実装されています：

  * `WetBulb` 湿球温度、実際には断熱飽和温度
  * `DewPoint` 雨点温度
  * `RelHum` 相対湿度
  * `HumRat` 湿度比 (kgの蒸気 / kgの乾燥空気)
  * `SpecHum` 比湿 (kgの蒸気 / kgの湿った空気)
  * `MolarFrac` 水蒸気のモル分率。

次のメソッドが実装されています：

  * `volume(MoistAir, T, HumType, h, P)` 比容積
  * `volumem(MoistAir, T, HumType, h, P)` モル容積
  * `density(MoistAir, T, HumType, h, P)` 密度
  * `enthalpy(MoistAir, T, HumType, h, P)` 比エンタルピー
  * `enthalpym(MoistAir, T, HumType, h, P)` モルエンタルピー
  * `entropy(MoistAir, T, HumType, h, P)` 比エントロピー
  * `entropym(MoistAir, T, HumType, h, P)` モルエントロピー
  * `compressfactor(MoistAir, T, HumType, h, P)` 圧縮因子。

比エンタルピー、エントロピー、および容積は、乾燥空気の質量に対して計算されることに注意する必要があります。したがって、1 J/kg は実際には 1 J/kg の乾燥空気に対するものです。
