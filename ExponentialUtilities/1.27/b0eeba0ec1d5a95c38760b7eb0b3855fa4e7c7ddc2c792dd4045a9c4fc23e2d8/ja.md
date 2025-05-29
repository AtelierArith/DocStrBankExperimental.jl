```
phi(z,k[;cache]) -> [phi_0(z),phi_1(z),...,phi_k(z)]
```

スカラー phi 関数を k までのすべての次数について計算します。

phi 関数は次のように定義されます。

$$
\varphi_0(z) = \exp(z),\quad \varphi_{k+1}(z) = \frac{\varphi_k(z) - 1}{z}
$$

数値的に不安定な再帰関係の代わりに、Sidje によって与えられた公式が使用されます（Sidje, R. B. (1998). Expokit: a software package for computing matrix exponentials. ACM Transactions on Mathematical Software (TOMS), 24(1), 130-156. 定理 1）。
