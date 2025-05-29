```
newton_lift(E::EllipticCurve, P::EllipticCurvePoint, reduction_map; max_iterations=7) -> Bool, EllipticCurvePoint
```

点 `Q` を返す `E` の、`reduction_map` によって `P` に還元されるかどうかとともに、その存在を示します。

$$
F
$$

を数体とし、$E$ を $F(t)$ 上の楕円曲線で、$F[t]$ に対して整合的であるとします。$O_F$ を $F$ の最大整域とし、$p$ を $O_F$ の素イデアル、$k$ をその残余体とします。$E$ が $(O_F)_p$ に対して整合的であり、$p$ で良い還元を持つと仮定します。

このアルゴリズムは、`P` を多変数ニュートン反復によって、素数 $p$ における $F$ の完備化の点に持ち上げます（ある有限の精度まで）。対応する小さな高さの点が `F` で計算され、結果が検証されます。

`max_iterations` に達しても `F` の点を認識できない場合はエラーをスローします。計算中の出力には `set_verbosity_level(:NewtonLift, 2)` を使用してください。

入力:

  * `E` – 楕円曲線 $E/F(t)$
  * `p` – $E/k(t)$ の点
  * `reduction map` – 標準的な準同型 $O_F \rightarrow k$
  * max_iterations – ニュートン反復ステップの最大数。高い値に設定すると計算が大幅に遅くなります。
