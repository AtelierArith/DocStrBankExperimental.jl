```
order(f, w)
```

与えられた補完の順序 $(v_1, v_2)$ を計算します。

$$
w=(w_1,w_2)
$$

における $f$ の $j$-番目の順序は、1変数のローレンツ多項式

$$
    u ↦ f(c_1^u^{δ_{1j}}, c_2^u^{δ_{2j}})
$$

のゼロの数（極の数を引いたもの）によって計算できます。これは単位円 $|u|=1$ の内部におけるものであり、$(c1, c2)$ は $Log(c1, c2) = w$ を満たす任意のベクトルです [^1]。

これを計算するために、[引数の原理](https://en.m.wikipedia.org/wiki/Argument_principle) を使用できます。これには、積分を再記述する必要があります（ここでは順序の最初の成分のみについて）

$$
rac{1}{2πi}∫_{|u|=1}rac{f'(e^{w_1}u, e^{w_2})}{f(e^{w_1}u, e^{w_2})}du
$$

変数変換を行うと、次のようになります。

$$
rac{1}{2πi}∫_0^{2π}rac{f'(e^{w_1}e^{iθ}, e^{w_2})}{f(e^{w_1}e^{iθ}, e^{w_2})}ie^{iθ}dθ
$$

[^1]: Forsberg, Mikael, Mikael Passare, and August Tsikh. "Laurent determinants and arrangements of hyperplane PolynomialAmoebas." Advances in mathematics 151.1 (2000): 45-70.

```
