```
dcount_buckets(ncats::Int, dInfo::Dinfo, nbuckets::Int, buckets::Dinfo)::Matrix{Int}
```

`dcount`と同様ですが、`buckets`でバケット化された`dInfo`内のアイテムをカウントして、`ncats`行と`nbuckets`列のカウントの行列を生成します。

ファイル内のクラスタ分布を決定するために`distributeFCSFileVector`と一緒に使用すると便利です。
