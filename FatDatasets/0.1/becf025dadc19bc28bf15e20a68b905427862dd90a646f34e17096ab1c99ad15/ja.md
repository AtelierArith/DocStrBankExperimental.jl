```julia
random_GMM(
    k,
    d;
    separation,
    centers_var,
    inter_intra_var_ratio,
    Dirichlet_parameter,
    intra_var,
    intra_var_balance,
    out_dic
)

```

`k` 個のガウスのランダム混合を次元 `d` で返します。生成プロセスに関する情報は、キーワード引数 `out_dic` に辞書を渡すことで取得できます。

次の引数のうち2つを同時に提供することができ（3つ目は自動的に計算されます）：

  * `separation`: ガウスの中心は、標準偏差 `separation × k^(1/d)` の正規分布に従って引かれます。
  * `intra_var`: 混合の各成分の分散（`intra_var_balance` が 1.0 に設定されている場合）。
  * `inter_intra_var_ratio`: クラスタ間分散とクラスタ内分散の比率。

デフォルトでは、2.5 の分離と 1.0 の内部分散が使用されます。

他のパラメータには次のものが含まれます：

  * `Dirichlet_parameter`: 異なるクラスタの重みのバランスを制御します。
  * `intra_var_balance`: 1.0（デフォルト値）より大きい場合、ランダムな分散が `intra_var` / `intra_var_balance` と `intra_var` × `intra_var_balance` の間で引かれます。

参照： [`GMMDataset`](@ref).
