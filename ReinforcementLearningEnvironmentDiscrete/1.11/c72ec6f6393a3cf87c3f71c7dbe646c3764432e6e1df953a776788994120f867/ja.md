```
`DiscreteMaze`は、幅`nx`と高さ`ny`を持ち、`nwalls`の壁と`ngoals`の目標位置を持つ`DiscreteMaze`を返します。報酬`goalreward`（異なる目標状態のための異なる報酬のリストまたはすべての目標に対する定数報酬）、移動のコスト`stepcost`（報酬 = -`stepcost`）があります。`stochastic = true`の場合、アクションは特定の確率で隣接状態に遷移し、`neighbourstateweight`がこの確率を制御します。
```
