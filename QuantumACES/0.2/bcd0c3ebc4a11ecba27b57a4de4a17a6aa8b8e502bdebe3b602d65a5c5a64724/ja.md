```
apply!(t::Tableau, l::Layer; return_measurements::Bool = false)
```

タブロー `t` に対してレイヤー `l` のすべてのゲートを実行し、`return_measurements` が `true` の場合は測定結果のリストを返します。
