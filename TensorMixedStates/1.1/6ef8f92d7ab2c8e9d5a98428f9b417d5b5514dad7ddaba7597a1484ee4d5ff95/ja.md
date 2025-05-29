`Evolve`のアルゴリズムタイプ

これは、与えられた次数の近似を得るために、指数近似WIまたはWIIを組み合わせた時間発展に対応します。

# 例

```
ApproxW(order = 2)                   order 2, WII
ApproxW(order = 4, w = 1)            order 4, WI
ApproxW(order = 4, n_symmetrize = 3) order 4, 3ステップごとにエルミート化
```
