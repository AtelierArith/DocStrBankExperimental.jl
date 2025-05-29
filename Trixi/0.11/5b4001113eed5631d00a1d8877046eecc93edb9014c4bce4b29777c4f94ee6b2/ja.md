```
TrafficFlowLWREquations1D
```

1D交通流の古典的なライトヒル-ウィザム-リチャーズ（LWR）モデル。車両密度は$u \in [0, 1]$で表され、最大可能速度（例えば、速度制限による）は$v_{\text{max}}$です。

$$
\partial_t u + v_{\text{max}} \partial_1 [u (1 - u)] = 0
$$

詳細については、例えば以下のセクション11.1を参照してください。

  * Randall LeVeque (2002)

有限体積法によるハイパーボリック問題 [DOI: 10.1017/CBO9780511791253](https://doi.org/10.1017/CBO9780511791253)
