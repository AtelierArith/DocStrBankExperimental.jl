```
RelativePermeabilities((kr1, kr2, ...))
```

単純な相対透過率の実装です。各相が次の形式の相対透過率を持つと仮定します：

$$
K_{r,phase} = F(S_{phase})
$$

`regions`キーワードを通じて複数の流体領域をサポートします。

# 例

単一領域：

```
kr1 = S -> S^2
kr2 = S -> S^3

kr = RelativePermeabilities((kr1, kr2))
```

二つの領域：

```
kr1_reg1 = S -> S^2
kr2_reg1 = S -> S^3

kr1_reg2 = S -> S^3
kr2_reg2 = S -> S^4

regions # ドメイン内の各セルに対して1または2のエントリを持つベクトルである必要があります

kr = RelativePermeabilities(((kr1_reg1, kr2_reg1), (kr1_reg2, kr2_reg2)), regions = regions)
```
