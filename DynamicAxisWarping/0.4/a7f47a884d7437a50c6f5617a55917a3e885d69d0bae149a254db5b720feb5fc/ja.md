```
dtw_cost(a::AbstractArray, b::AbstractArray, dist::Distances.SemiMetric, r::Int; best_so_far = Inf, cumulative_bound = Zeros(length(a)))
```

2つのシーケンス間の距離を測定するために動的時間ワーピングを実行します。

最大ワーピング半径 `r` で `a` と `b` の間のDTWコストを計算します。早期停止を可能にするために、`best_so_far` と `cumulative_bound` の値を提供することができます。

# キーワード引数:

  * `best_so_far`: これまでに得られた最良のコスト値（オプション）
  * `cumulative_bound`: a と b と同じ長さのベクトル（オプション）
  * `s1`: 長さ 2r+1 のオプションのストレージベクトルで、アロケーションを保存するために使用できます。
  * `s2`: 長さ 2r+1 のオプションのストレージベクトルで、アロケーションを保存するために使用できます。

2つのベクトル `s1, s2` を提供することはあまり時間を節約しませんが、関数を完全にアロケーションフリーにします。スレッド化されたコンテキストで役立つことがあります。

[`dtw`](@ref) および [`dtwnn`](@ref) も参照してください。このコードは https://www.cs.ucr.edu/~eamonn/UCRsuite.html からインスパイアを受けました。
