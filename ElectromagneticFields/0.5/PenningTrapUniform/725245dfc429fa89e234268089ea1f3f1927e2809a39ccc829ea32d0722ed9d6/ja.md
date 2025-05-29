ペニングトラップと一様磁場の (x,y,z) 座標。Yanyan Shi, Yajuan Sun, Yulei Wang, Jian Liu による「Study of adaptive symplectic methods for simulating charged particle dynamics」、Journal of Computational Dynamics 6, 429-448, 2019 に基づいています。

ベクトルポテンシャルの共変成分は次のように与えられます。

$$
A (x,y,z) = B_0 \, ( 0, x, 0)^T ,
$$

これにより、共変成分を持つ磁場が得られます。

$$
B (x,y,z) = B_0 \, ( 0, 0, 1)^T ,
$$

そして、静電ポテンシャルは次のように与えられます。

$$
\varphi (x,y,z) = E_0 \, ( x^2 / 2 + y^2 / 2 - z^2) ,
$$

これにより、共変成分を持つ電場が得られます。

$$
E (x,y,z) = E_0 \, ( x, y, - 2 z)^T .
$$

パラメータ：

  * `B₀`: B-フィールド強度
  * `E₀`: E-フィールド強度
