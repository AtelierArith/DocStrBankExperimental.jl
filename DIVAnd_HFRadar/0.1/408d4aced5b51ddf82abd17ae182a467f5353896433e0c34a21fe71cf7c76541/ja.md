```
DIVAndrun_HFRadar(mask,h,pmn,xyi,xyobs,robs,directionobs,len,epsilon2;...)
```

HFレーダーの現在の分析とDIVAndおよび速度制約。入力パラメータは次のとおりです。

  * `mask`: 海のポイントに対してtrue（陸のポイントに対してfalse）（3D配列）
  * `h`: メートル単位の深さ（3D配列）
  * `pmn`: ローカル解像度の逆数（3つの3D配列のタプル）
  * `xyi`: 分析グリッドの座標（3つの3D配列のタプル）
  * `xyobs`: 観測の座標（3つのベクトルのタプル）
  * `robs`: 放射速度（ベクトル）
  * `directionobs`: 測定された方向の角度α（度単位）（ベクトル）で、次のようになります。

$$
u_{obs}  \sin(α) + v_{obs}  \cos(α) ≈ r_{obs}
$$

  * `len`: 相関長（スカラーのタプル）
  * `epsilon2`: 背景推定の誤差分散に対する観測の誤差分散。

## オプションの入力パラメータ

  * `eps2_boundary_constraint`（デフォルト -1）：境界制約の相対誤差分散
  * `eps2_div_constraint`（デフォルト -1）：発散制約の相対誤差分散
  * `eps2_Coriolis_constraint`（デフォルト -1）：コリオリ制約の相対誤差分散
  * `f`（デフォルト 0.001 s⁻¹）：コリオリパラメータ。緯度$φ$の場合、地球上では次のようになります：

$$
\begin{aligned}
    Ω =& 7.2921 \; 10^{-5} rad/s \\
    f =& 2 Ω \sin(φ)
\end{aligned}
$$

  * `g`（デフォルト 0. m/s²）：重力による加速度。gがゼロの場合、表面圧力は考慮されず、そうでない場合はgを9.81に設定する必要があります。
  * `ratio`（デフォルト 100）：正規化係数
  * `lenη`（デフォルト 0, 0, 24 * 60 * 60. * 10）：表面の高さに対する空間と時間の相関長
  * `residual`: robsと同じサイズの配列で、残差（出力）

## 方向の規約

方位βは、レーダー局（*）と測定点（+）の間の北から時計回りに数えた角度であり、方向αは測定点での北とレーダー局を指すベクトルとの間の角度です。

```
                ↑ /
                |/
         ↑      +--→ 現在のベクトル (u,v)
  北      |     / 測定点
         |    /
         |   /
         |  /
         |β/
         |/
         *
   レーダー局
```

極から十分に離れている場合、次のようになります。

$$
α ≈ β + 180°
$$

$$
u
$$

の緯度成分と$v$の経度成分は、放射電流$r$と方向$α$によって次のように関連しています。

$$
\begin{aligned}
u =& r \sin(α) \\
v =& r \cos(α) \\
\end{aligned}
$$

$$
\begin{aligned}
r =& u  \sin(α) + v  \cos(α) \\
\tan(α) &= {u \over v}
\end{aligned}
$$

HFレーダーデータの場合、rは速度がレーダーサイトに*向かっている*場合に正です。r、u、v、方向およびβは、ruvファイルのCODAR規約と一致しています[1,2]：

> 正の放射速度はSeaSondeに向かって移動し、負の放射速度はSeaSondeから離れて移動します。


!!! note
    コリオリ力の制約と表面圧力勾配の制約には、時間次元を含める必要があります。


!!! info
    入力時、方向角$α$は度（0 - 360°）で表されます。


!!! info
    `ERROR: PosDefException: matrix is not positive definite; Cholesky factorization failed.`というエラーが表示された場合、特に相関、スケールファクター`pmn`および`epsilon2`の入力パラメータの値を確認する必要があります。


[1] [CODAR放射データに使用されるファイル形式](https://web.archive.org/web/20181009090405/https://cordc.ucsd.edu/projects/mapping/documents/radFileFormats_20050408.pdf)

[2] [SeaSondesの技術者情報ページ](https://web.archive.org/web/20200125080518/http://support.codar.com/Technicians_Information_Page_for_SeaSondes/Docs/GuidesToFileFormats/File_LonLatUV_RDL_TOT_ELP.pdf) ```
