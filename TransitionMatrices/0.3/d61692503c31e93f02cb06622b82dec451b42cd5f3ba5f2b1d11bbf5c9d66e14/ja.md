```
orientation_average(𝐓::AbstractTransitionMatrix{CT, N}, pₒ; Nα = 10, Nβ = 10, Nγ = 10) where {CT, N}
```

遷移行列の方向平均を数値積分を用いて計算します。方向分布関数 $p_o(\alpha,\beta,\gamma)$ が与えられます。

$$
\langle T_{m n m^{\prime} n^{\prime}}^{p p^{\prime}}(L)\rangle = \int_0^{2\pi}\mathrm{d}\alpha\int_0^{\pi}\mathrm{d}\beta\sin\beta\int_0^{2\pi}\mathrm{d}\gamma p_o(\alpha,\beta,\gamma) T_{m n m^{\prime} n^{\prime}}^{p p^{\prime}}(L; \alpha,\beta,\gamma)
$$

パラメータ:

  * `𝐓`: 方向平均を取るT行列。
  * `pₒ`: 方向分布関数。$\sin\beta$の部分はすでに含まれています。
  * `Nα`: $\alpha$の数値積分に使用される点の数。デフォルトは10です。
  * `Nβ`: $\beta$の数値積分に使用される点の数。デフォルトは10です。
  * `Nγ`: $\gamma$の数値積分に使用される点の数。デフォルトは10です。

!!! note
    これはフォールバックメソッドであり、対称性を利用していないため、遅くなることが予想されます。指定されたバージョンのこの関数を使用するか、T行列と方向分布関数の組み合わせに適したバージョンがない場合は、自分で実装する必要があります。

    また、`Nα`、`Nβ`、`Nγ`の収束を手動でテストする必要があるかもしれません。いずれかが小さすぎると、結果に大きな誤差が生じます。

