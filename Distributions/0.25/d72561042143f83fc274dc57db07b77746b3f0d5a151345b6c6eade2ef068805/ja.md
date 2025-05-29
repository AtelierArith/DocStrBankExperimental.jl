```
product_distribution(dists::AbstractVector{<:Normal})
```

一変量正規分布を積み重ねることで多変量正規分布を作成します。

結果として得られる[`MvNormal`](@ref)型の分布は対角共分散行列を持ちます。
