軸対称トカマク平衡を (x,y,z) 座標系で、ベクトルポテンシャルの共変成分が次のように与えられます。

$$
A (x,y,z) = \frac{1}{2} \frac{B_0}{q_0} \, \bigg( \frac{q_0 R_0 x z - r^2 y}{R^2} , \, \frac{q_0 R_0 y z + r^2 x}{R^2} , \, - q_0 R_0 \, \ln \bigg( \frac{R}{R_0} \bigg) \bigg)^T ,
$$

これにより、磁場の共変成分は次のようになります。

$$
B (x,y,z) = \frac{B_0}{q_0} \, \bigg( - \frac{q_0 R_0 y + x z}{R^2} , \, \frac{q_0 R_0 x - y z}{R^2} , \, \frac{R - R_0}{R} \bigg)^T ,
$$

ここで $R = \sqrt{ x^2 + y^2 }$ および $r = \sqrt{ (R - R_0)^2 + z^2 }$ です。

パラメータ：

  * `R₀`: 磁気軸の位置
  * `B₀`: 磁気軸でのB場
  * `q₀`: 磁気軸での安全係数
