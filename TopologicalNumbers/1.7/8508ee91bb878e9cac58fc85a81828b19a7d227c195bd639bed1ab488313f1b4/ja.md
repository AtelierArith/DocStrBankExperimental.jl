Shiozaki method [Shiozaki2023discrete](@cite)

# 定義

$$
\mathbb{Z}_{2}
$$

数の $2n$ 番目（および $2n-1$ 番目）バンド $\nu_{n}$ は次のように定義されます。

$$
\nu_{n}=F_{n}-\left(P_{n}(0)-P_{n}(\pi)\right)
$$

$$
F_{n}
$$

は $\mathrm{BZ}'$ における $n$ 番目のバンドのベリー流束です。範囲 $\mathrm{BZ}'$ は $\bm{k}\in[0,2\pi]\times[0,\pi]$ で、BZ（ブリルアンゾーン）の半分です。

$$
F_{n}=\frac{1}{2\pi}\sum_{\bm{k}\in\mathrm{BZ}'}\mathrm{Im}\left[\mathrm{Log}\left[U_{n,1}(\bm{k})U_{n,2}(\bm{k}+\bm{e}_{1})U_{n,1}^{*}(\bm{k}+\bm{e}_{2})U_{n,1}^{*}(\bm{k})\right]\right]
$$

$$
P_{n}(k_{2})
$$

は波数 $k_{2}$ における時間反転偏極です。

$$
P_{n}(k_{2})=\frac{1}{2\pi}\frac{\mathrm{Pf}[\omega(0,k_{2})]}{\mathrm{Pf}[\omega(\pi,k_{2})]}\sum_{k_{1}=0}^{\pi-e_{1}}U_{n,1}(\bm{k})
$$

$$
U_{n,i}(\bm{k})
$$

は波数 $\bm{k}$ におけるリンク変数です。$\bm{e}_{i}$ は単位ベクトルです。

$$
U_{n,i}(\bm{k})=\braket{\Psi_{n}(\bm{k})|\Psi_{n}(\bm{k}+\bm{e}_{i})}
$$

$$
\ket{\Psi_{n}(\bm{k})}
$$

は $2n$ 番目（および $2n-1$ 番目）バンドの波動関数です。$\omega(\bm{k})$ は次のように与えられるユニタリ行列です。

$$
\omega(\bm{k})=\bra{\Psi(-\bm{k})}T\ket{\Psi(\bm{k})}
$$

$$
T
$$

は時間反転演算子です。
