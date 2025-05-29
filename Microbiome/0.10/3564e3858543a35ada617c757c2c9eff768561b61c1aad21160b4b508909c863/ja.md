```
prevalence(a::AbstractArray{<:Real}, minabundance::Real=0.0)
prevalence(at::AbstractAbundanceTable, minabundance::Real=0.0)
```

最小値以上の値の割合を返します。最小の豊富さが0の場合、ゼロでない値の割合を返します。

`AbstractAbundanceTable`で使用した場合、各`feature`に対する`sample`のプレバレンス値を返します。
