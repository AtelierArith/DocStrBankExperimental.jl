```
simulate_block_covariance(groups, ρ, γ, num_v, w)
```

`Dai & Barber 2016, The knockoff filter for FDR control in group-sparse and multitask regression`に似たブロック共分散行列をシミュレートします。つまり、すべての対角要素は1になり、グループ内の相関は`ρ`、グループ間の相関は`ρ*γ`になります。

# 入力

  * `groups`: グループメンバーシップのベクトル
  * `ρ`: グループ内相関
  * `γ`: グループ間相関

# オプション引数

  * `num_v`: 追加されたランク1更新の数 `Σ + v1*v1' + ... + vn*vn'` で、`v`はiid `N(0, w)`（デフォルトは0）
  * `w`: `num_v`で使用されるランク1更新の分散（デフォルトは1）
