```
description!(io::CSeis, kwargs...)
```

既存のCloudSeisデータセットのプロパティの制限された変更。

# オプショナルキーワード引数

  * `axis_lengths = nothing`  軸の長さ（3次元目およびそれ以上）のサイズを増やします[1]。
  * `dataproperties = nothing`  データセットのデータプロパティを`dataproperties`で置き換えます。[2]
  * `dataproperties_add = nothing`  データセットのデータプロパティに`dataproperties_add`を追加します。[2]

# 注意事項

  * [1] `axis_lengths`は`size(io)`と同じ長さでなければなりません。さらに、`prod(axis_lengths[3:end])`

は`prod(size(io)[3:end])`より大きくなければならず、`axis_lengths[i]`はi∈(1..ndims(io)-1)に対して`size(io,i)`と等しくなければなりません。

  * [2] `dataproperties`または`dataproperties_add`のいずれか一方のみを指定できます。
