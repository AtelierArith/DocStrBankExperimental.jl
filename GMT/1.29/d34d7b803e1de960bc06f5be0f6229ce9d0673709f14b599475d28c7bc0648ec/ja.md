p = sortslicesperm(A; dims=1, kws...)

`sortslices`と同様ですが、代わりにインデックス`p`を返します。これは`A[p, :] == sortslices(A; dims=1, kws...)`となります。
