```
unit_group(K::PadicField; n_quo::Int = -1) -> FinGenAbGroup, Map
```

グループ $U$ とマップ $f: U \to\K^*$ を返します。$U$ は $K$ の精度までの単位群の近似です。より正確には、もし `K^* = \langle p\rangle  \times \mathbbb F_p^* \times 1+p\mathbbb Z_p` であれば、$U$ は $\mathbbb Z \times \mathbbb Z/(p-1) \times \mathbbb Z/p^{(k-1)}$ に同型になります。

`n_quo` が与えられ、かつ正の場合、$\mathbbb F_p^*$ は `n_quo`-乗の剰余に置き換えられます。（有限体におけるコストのかかる離散対数を避けるため）
