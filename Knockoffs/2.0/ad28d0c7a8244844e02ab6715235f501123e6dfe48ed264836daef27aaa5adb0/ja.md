```
threshold(w::AbstractVector, q::Number, [method=:knockoff], [m::Int=1])
```

τ > 0 の閾値を選択するために `τ` を次のいずれかに設定します。 τ = min{ t > 0 : {#j: w[j] ≤ -t} / {#j: w[j] ≥ t} ≤ q }        (`method=:knockoff`) τ = min{ t > 0 : (1 + {#j: w[j] ≤ -t}) / {#j: w[j] ≥ t} ≤ q }  (`method=:knockoff`)

# 入力

  * `w`: 特徴の重要な統計のベクトル
  * `q`: 目標FDR（0と1の間）
  * `method`: `:knockoff` または `:knockoff_plus`（デフォルト）
  * `rej_bounds`: 考慮する上位Wの値の数（デフォルト = 10000）

# 参考文献:

「Panning for Gold: Model-X Knockoffs for High-dimensional Controlled Variable Selection」Candes, Fan, Janson, and Lv (2018) の式 3.10 (`method=:knockoff`) または 3.11 (`method=:knockoff_plus`)
