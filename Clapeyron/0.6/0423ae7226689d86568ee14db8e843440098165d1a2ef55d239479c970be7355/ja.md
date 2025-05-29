```
AssocOptions(;rtol = 1e-12,atol = 1e-12,max_iters = 1000,dampingfactor = 0.5,combining =:nocombining)
```

ソルバーのための反応サイトの反復パラメータを含む構造体。combiningオプションは、結合強度に適用される結合ルールのタイプを制御します：

  * `nocombining`（デフォルト）。結合ルールを実行しません。
  * `:cr1`: "結合ルール - 1":   `ε[i,j][a,b] = (ε[i,i][a,b] + ε[j,j][a,b])/2   β[i,j][a,b] = √(β[i,i][a,b] * β[j,j][a,b])`
  * `:esd`,`:elliott`: エリオット–スレッシュ–ドノヒュー結合ルール:   `ε[i,j][a,b] = (ε[i,i][a,b] + ε[j,j][a,b])/2   β[i,j][a,b] = √(β[i,i][a,b] * β[j,j][a,b]) * (σ[i]*σ[j]/σ[i,j])^3`
  * `:esd_runtime`,`:elliott_runtime`: ランタイムで実行される結合ルール:   `Δ[i,j][a,b] = √(Δ[i,i][a,b] * Δ[j,j][a,b])`
  * `:dufal`,`mie15`: `SAFTVRMie15`に使用される結合ルール   `ε[i,j][a,b] = (ε[i,i][a,b] + ε[j,j][a,b])/2   β[i,j][a,b] = (∛β[i,i][a,b] + ∛β[j,j][a,b])^3 / 8`

!!! info "結合スキームの重要性"
    すべての結合ルールは暗黙的に `Δ(i,i,a,b)` と `Δ(j,j,a,b)` がゼロでないことを要求します。つまり、自己結合しない成分は結合されません。

