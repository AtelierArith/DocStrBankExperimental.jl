```
new_matrix(A::AbstractMatrix, opts::Dict{Symbol,Any}=()) -> ps_data
```

行列を擬似スペクトルで使用される補助データ構造に処理します。

# オプション

  * `:direct::Bool`: 直接アルゴリズムの使用を強制しますか？
  * `:keep_sparse::Bool`: `A`が大きくなくてもスパース行列コードを使用しますか？
  * `:real_matrix::Bool`: `A`を実行列とユニタリ同等と見なしますか？
  * `:verbosity::Int`: 明白
  * `:eigA`: 既に知られている場合の`A`の固有値
  * `:proj_lev`: 投影レベル（`psa_compute`を参照）
  * `:npts`: 擬似スペクトルを計算およびプロットするためのグリッドのエッジ長
  * `:arpack_opts::ArpackOptions`: （型の説明を参照）
  * `:levels::Vector{Real}`: 等高線レベル（自動選択を望まない場合）
  * `:ax::Vector{Real}(4)`: 計算のためのバウンディングボックス `[xmin,xmax,ymin,ymax]`
  * `:scale_equal::Bool`: スペクトルポートレートのために等方的な軸を強制しますか？
  * `:threaded::Bool`: `Z`の値をJuliaスレッドに分散させますか？
