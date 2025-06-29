ライン停電分配係数 (LODF) マトリックスは、ラインのフローの変化がシステム内の他のラインのフローにどのように影響するかの感度係数を集めます。

# 引数

  * `data<:AbstractArray{Float64, 2}`:       転置された LODF マトリックス。
  * `axes<:NTuple{2, Dict}`:       各行/列に関連するブランチの名前を含む2つの同一のベクターを含むタプル。
  * `lookup<:NTuple{2, Dict}`:       ブランチをその列挙インデックス（行番号および列番号）にマッピングする2つの同一の辞書を含むタプル。
  * `tol::Base.RefValue{Float64}`:       マトリックスをスパース化するために使用される許容値（この閾値未満の絶対値を持つ要素を削除）。
  * `radial_network_reduction::RadialNetworkReduction`:       マトリックスを評価する際に削除された放射状ブランチとリーフバスを含む構造体。
