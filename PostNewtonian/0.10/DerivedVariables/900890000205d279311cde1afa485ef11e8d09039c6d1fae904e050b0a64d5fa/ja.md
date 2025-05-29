```
χₚ(s)
chi_p(s)
```

システムの有効な歳差スピンパラメータ。

この量には文献において*2つの異なる*定義が存在することに注意してください。[元の定義](https://arxiv.org/abs/1408.1810)（$M_1 \geq M_2$の規約に変換されたもの）は次のようになります。

$$
\begin{gathered}
A_1 = 2 + \frac{3M_2}{2M_1} \\
A_2 = 2 + \frac{3M_1}{2M_2} \\
\chi_{\mathrm{p}} \colonequals \frac{1}{A_1 M_1^2}
\mathrm{max}\left(A_1 S_{1\perp}, A_2 S_{2\perp} \right).
\end{gathered}
$$

検出時代の初期の論文で、[LIGOコラボレーションはこの定義を使用しました](https://arxiv.org/abs/1606.01210)。

しかし、[より最近の論文](https://arxiv.org/abs/2010.04131)では、実質的にこの量の$M_1^2$倍として再定義されています。$q = M_2/M_1 \leq 1$という規約を使用すると、定義はより簡潔に次のように書くことができます。

$$
\chi_{\mathrm{p}} \colonequals \mathrm{max} \left(
    \chi_{1\perp}, \chi_{2\perp} q \frac{4q+3}{4+3q}
\right).
$$

再度、[LIGO/Virgo/KAGRA](https://arxiv.org/abs/2111.03606)によるより最近の論文がこの規約を使用しています。

この傾向に従って、この関数は後者の定義を使用します。
