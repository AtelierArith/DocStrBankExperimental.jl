```
resample_elwise(uvd::UVAL_COLLECTION_TYPES, 
    constraint::Union{SamplingConstraint, Vector{SamplingConstraint}},
    n::Int)
```

`uvals`の各要素を`n`回再サンプリングします。返されるベクトルのi番目のエントリは、提供された`constraint`(s)に従って最初に`uvals[i]`のサポートを切り詰めた後に引き出された`uvals[i]`の`n`個のユニークなドローからなる`n`要素のベクトルです。
