```
getsamples(
  M::Union{LPDO,MPO,ITensor},
  preps::Matrix,
  bases::Matrix,
  nshots::Int;
  kwargs...
)
```

入力状態 `preps` と測定 `bases` のセットに従ってプロセス測定データのセットを生成し、各構成ごとに `nshots` 測定を行います。単一の測定では、入力状態 $|\xi\rangle=\otimes_j|\xi_j\rangle$ がチャネル $M$ に従って進化し、次に与えられた測定基準で測定されます。最終状態が基準 $U$ で定義された結果 $\sigma = (\sigma_1,\sigma_2,\dots)$ を返す確率は次のように与えられます。

$$
P(\sigma|\xi) = \text{Tr}\big[(\rho_\xi^T\otimes 1)\Lambda_{M} \big]
$$

ここで、$\rho_\xi = |\xi\rangle\langle\xi|$ であり、$\Lambda_M$ はチョイ行列です。
