```
pure_nash(nfg; ntofind=Inf, tol=1e-8)
```

通常形ゲームのすべての純粋戦略ナッシュ均衡を見つけます。純粋戦略ナッシュが存在しない場合は空の配列を返します。

現在はブルートフォースアルゴリズムを使用していますが、将来的には変更されることを期待しています。

# 引数

  * `nfg::NormalFormGame`: N人プレイヤーのNormalFormGameのインスタンス。
  * `ntofind::Inf`: 見つけるべき純粋戦略ナッシュ均衡の最大数; デフォルトは `prod(nfg.nums_actions)` です。
  * `tol::Real` : 最良応答アクションを決定するために使用される許容誤差。

# 戻り値

  * `ne::Vector{NTuple{N,Int}}`: 純粋戦略ナッシュ均衡のベクター。
