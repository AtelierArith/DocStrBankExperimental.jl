```
make_df(algs = [MergeSort, QuickSort]; ...)
```

各行がキーワード引数の直積によって指定されたソートタスクであるデータフレームを作成します。

# 引数

  * `algs::AbstractVector{<:Base.Sort.Algorithm} = [MergeSort, QuickSort]`:   テストするソートアルゴリズム
  * `unstable::AbstractVector{<:Base.Sort.Algorithm} = [QuickSort]`:   不安定であることが許可されているアルゴリズム

直積の軸

  * `Types::AbstractVector{<:Type} = SortMark.BitTypes`:   要素の型
  * `lens::AbstractVector{<:Integer} = SortMark.lengths()`:   ソートされる要素の数
  * `orders::AbstractVector{<:Ordering} = SortMark.orders`:   ソートする順序
  * `sources::AbstractDict{<:Any, <:Function} = SortMark.sources`:   入力データを生成する手続き

ベンチマーク時間

  * `seconds::Union{Real, Nothing} = .005`:   各行の最大ベンチマーク時間。推定ベンチマーク実行時間のために sum(df.seconds) を計算します
  * `samples::Union{Nothing, Integer} = nothing`:   各行の最大サンプル数。推定ベンチマーク実行時間のために sum(df.seconds) を計算します

`seconds` または `samples` を `nothing` に設定すると、その制限が解除されます。
