```
solve_s_group(Σ, groups, method; [m=1], kwargs...)
```

グループノックオフ問題を解決し、`(m+1)/m*Σ - S ⪰ 0` を満たすブロック対角行列 S を返します。ここで `m` は特徴ごとのノックオフの数です。

# 入力

  * `Σ`: `Symmetric` キーワードでラップされた一般的な共分散行列
  * `groups`: グループメンバーシップのベクター、連続している必要はありません
  * `method`: ノックオフを構築するための方法。オプションには以下が含まれます

      * `:maxent`: (推奨) 完全一般的最大エントロピーグループノックオフ用
      * `:mvr`: 完全一般的最小分散ベースの再構成可能性 (MVR) グループノックオフ用
      * `:equi`: 等相関ノックオフ用。これは `Dai R, Barber R. The knockoff filter for FDR control in group-sparse and multitask regression. International conference on machine learning 2016 Jun 11 (pp. 1851-1859). PMLR.` で提案された方法論です。
      * `:sdp`: 座標降下に基づく完全一般的 SDP グループノックオフ
      * `:sdp_subopt`: 各ブロック `S_{i} = γ_i * Σ_{ii}` を選択します。これは、Dai と Barber 2016 で提案された等相関グループノックオフのアイデアを少し一般化したものです。
      * `:sdp_block`: 各ブロックが内部点ソルバーを使用して正確に解かれる完全一般的 SDP グループノックオフ。
  * `m`: 変数ごとのノックオフの数、デフォルトは 1。
  * `kwargs`: 特定の方法に利用可能な追加引数。たとえば、より緩やかな収束許容を使用するには、`tol = 0.001` を指定します。利用可能なオプションのリストについては、[`solve_group_mvr_hybrid`](@ref)、[`solve_group_max_entropy_hybrid`](@ref)、[`solve_group_sdp_hybrid`](@ref)、または [`solve_group_equi`](@ref) を参照してください。

# 出力

  * `S`: `(m+1)/m*Σ - S ⪰ 0` および `S ⪰ 0` を満たすように解かれた行列
  * `γ`: 等相関および最適でないノックオフ構築の場合にのみ非空のベクター。これは `S_{gg} = γΣ_{gg}` となる γ の値に対応します。したがって、等相関の場合、ベクターの長さは 1 です。SDP の場合、ベクターの長さはグループの数に等しいです。
  * `obj`: `S` に与えられた最終 SDP/MVR/ME 目的値。等相関グループノックオフおよびシングルトン (非グループ化ノックオフ) は、目的値がないか、目的を評価する必要がないため 0 を返します。

# 警告

この関数は `Σ` の列/行を入れ替える可能性があり、最後に元に戻します。したがって、同じ `Σ` に対して `solve_s_group` を同時に呼び出すべきではありません。たとえば、マルチスレッドの for ループ内での呼び出しは避けてください。グループが連続している場合、入れ替えは発生しません。
