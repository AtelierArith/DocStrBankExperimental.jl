```
constraints_list(P::VPolytope)
```

### アルゴリズム

1次元および2次元の集合については、それぞれ`Interval`または`VPolytope`に変換し、対応する`constraints_list`関数を呼び出します。高次元の集合については、`tohrep`を使用して制約表現を計算し、対応する`constraints_list`関数を呼び出します。
