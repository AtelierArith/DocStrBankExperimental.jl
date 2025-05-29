```
get_pflow_branch(data, model, branch_idx, year_idx, hour_idx)
```

ブランチの合計電力フローを返します。

  * branch*idx*が正の場合、正の電力フローはブランチテーブルに記載された方向 f*bus -> t*bus です。これは f_bus からの電力フローを測定しています。
  * branch*idx*が負の場合、正の電力フローは逆方向、t*bus -> f*bus であり、ブランチテーブルに記載されています。これは t_bus からの電力フローを測定しています。
  * モデルが最適化された後に変数の値を取得するために、この関数を value() でラップします。次のようにします: value.(get*pflow*branch)。
