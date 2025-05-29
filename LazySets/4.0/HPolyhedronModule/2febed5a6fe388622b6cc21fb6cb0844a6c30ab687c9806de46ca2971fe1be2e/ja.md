```
remove_redundant_constraints!(P::HPoly{N}; [backend]=nothing) where {N}
```

多面体の制約表現から冗長な制約を削除します。多面体はインプレースで更新されます。

### 入力

  * `P`       – 多面体
  * `backend` – （オプション、デフォルト: `nothing`）線形計画を解くために使用されるバックエンド

### 出力

メソッドが成功した場合は`true`を返し、多面体`P`は冗長な制約を削除することで修正されます。制約が非実現可能な場合、`P`が空であると検出された場合は`false`を返します。

### 注意事項

`backend`が`nothing`の場合、`default_lp_solver(N)`がデフォルトとして使用されます。

### アルゴリズム

詳細については`remove_redundant_constraints!(::AbstractVector{<:HalfSpace})`を参照してください。
