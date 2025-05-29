```
FormFactor(ion::String; g_lande=2)
```

与えられた磁気イオンと電荷状態のための磁気形状因子。[`intensities`](@ref)に渡すと、散乱ベクトルの大きさ $|𝐪|$ に基づいて構造因子の強度を再スケールします。

パラメータ `ion` は次の文字列のいずれかでなければなりません：

```
Am2, Am3, Am4, Am5, Am6, Am7, Au1, Au2, Au3, Au4, Au5, Ce2, Co0, Co1, Co2, Co3,
Co4, Cr0, Cr1, Cr2, Cr3, Cr4, Cu0, Cu1, Cu2, Cu3, Cu4, Dy2, Dy3, Er2, Er3, Eu2,
Eu3, Fe0, Fe1, Fe2, Fe3, Fe4, Gd2, Gd3, Hf2, Hf3, Ho2, Ho3, Ir0a, Ir0b, Ir0c,
Ir1a, Ir1b, Ir2, Ir3, Ir4, Ir5, Ir6, Mn0, Mn1, Mn2, Mn3, Mn4, Mn5, Mo0, Mo1, Nb0,
Nb1, Nd2, Nd3, Ni0, Ni1, Ni2, Ni3, Ni4, Np3, Np4, Np5, Np6, Os0a, Os0b, Os0c,
Os1a, Os1b, Os2, Os3, Os4, Os5, Os6, Os7, Pd0, Pd1, Pr3, Pt1, Pt2, Pt3, Pt4,
Pt5, Pt6, Pu3, Pu4, Pu5, Pu6, Re0a, Re0b, Re0c, Re1a, Re1b, Re2, Re3, Re4, Re5,
Re6, Rh0, Rh1, Ru0, Ru1, Sc0, Sc1, Sc2, Sm2, Sm3, Ta2, Ta3, Ta4, Tb2, Tb3, Tc0,
Tc1, Ti0, Ti1, Ti2, Ti3, Tm2, Tm3, U3, U4, U5, V0, V1, V2, V3, V4, W0a, W0b,
W0c, W1a, W1b, W2c, W3, W4, W5, Y0, Yb2, Yb3, Zr0, Zr1
```

末尾の数字はイオン化状態を示します。例えば、`"Fe0"` は中性の鉄原子を示し、`"Fe2"` は `Fe²⁺` を示します。複数の電子配置が可能な場合、末尾の文字（`a`, `b`, ...）で区別されます。この文字を省略すると、情報を含むエラーが表示されます。

```
FormFactor("Ir0")

ERROR: 電子配置に従って形状因子を明確にしてください：
    "Ir0a" -- 6s⁰5d⁹
    "Ir0b" -- 6s¹5d⁸
    "Ir0c" -- 6s²5d⁷
```

双極子近似（小 $|𝐪|$）では、形状因子は次のようになります。

$$
F(s) = ⟨j_0(s)⟩ + [(2-g)/g] ⟨j_2(s)⟩
$$

,

ここで $s = |𝐪|/4π$ であり、Landé $g$-因子を含みます。$⟨j_l(s)⟩$ は磁気双極子の $l$ 番目の球面ベッセル関数の放射平均です。詳細は文献 [1] に記載されています。

標準近似表はガウス展開を含みます。

$$
⟨j_0(s)⟩ = A e^{-as^2} + B e^{-bs^2} + C e^{-cs^2} + D e^{-ds^2} + E
$$

および

$$
⟨j_2(s)⟩ = (A e^{-as^2} + B e^{-bs^2} + C e^{-cs^2} + D e^{-ds^2} + E) s^2.
$$

3d、4d、希土類、アクチニウムイオンについて、SunnyはP. J. Brownの改訂表を使用します。これはMcPhaseパッケージ [2] に文書化されています。5dイオンについては、SunnyはKobayashi、Nagao、Itoの表を使用します [3]。

2つの特別な $𝐪$-独立の形状因子値が利用可能です：`one(FormFactor)` と `zero(FormFactor)`。最初のものは磁気イオンを完璧な点粒子として理想化し、2番目のものは磁気イオンからのすべての寄与をゼロにします。

## 参考文献

1. [P. J. Brown, The Neutron Data Booklet, 2nd ed., Sec. 2.5 *Magnetic Form Factors* (2003)](https://www.ill.eu/sites/ccsl/ffacts/ffachtml.html).
2. [McPhase documentation](https://www2.cpfs.mpg.de/~rotter/homepage_mcphase/manual/node137.html) の係数表。
3. [K. Kobayashi, T. Nagao, M. Ito, *Radial integrals for the magnetic form factor of 5d transition elements*, Acta Cryst. A, **67**, 473–480 (2011)](https://doi.org/10.1107/S010876731102633X).
