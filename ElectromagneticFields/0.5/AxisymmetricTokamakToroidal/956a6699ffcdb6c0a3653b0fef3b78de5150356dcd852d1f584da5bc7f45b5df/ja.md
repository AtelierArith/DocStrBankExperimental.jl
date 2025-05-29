軸対称トカマク平衡を(r,θ,ϕ)座標系で表し、ベクトルポテンシャルの共変成分は次のように与えられます。

$$
A (r, \theta, \phi) = B_0 \, \bigg( 0 , \, \frac{r R_0}{\cos (\theta)} - \bigg( \frac{R_0}{\cos (\theta)} \bigg)^2 \, \ln \bigg( \frac{R}{R_0} \bigg) , \, - \frac{r^2}{2 q_0} \bigg)^T ,
$$

これにより、共変成分を持つ磁場は次のようになります。

$$
B (r, \theta, \phi) = \frac{B_0}{q_0} \, \bigg( 0 , \, \frac{r^2}{R}, \, q_0 R_0 \bigg)^T ,
$$

ここで、$R = R_0 + r \cos \theta$です。

パラメータ：

  * `R₀`: 磁気軸の位置
  * `B₀`: 磁気軸でのB場
  * `q₀`: 磁気軸での安全係数
