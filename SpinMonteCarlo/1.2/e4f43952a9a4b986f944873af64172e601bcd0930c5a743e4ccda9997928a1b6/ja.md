```
Jackknife(f::Function, jks::Jackknife...)

`f`を`jks`に適用することでジャックナイフの観測可能値を構築します。
例えば、`Jackknife(mean, jk1, jk2, jk3)`は`jk1`、`jk2`、および`jk3`の平均のジャックナイフ観測可能値を返します。
```
