```
present(t::Union{Real, Missing}, minabundance::Real=0.0)
present(at::AbstractAbundanceTable, minabundance::Real=0.0)
```

与えられた（ゼロ以外の）値が最小値以上であるかどうかを確認します。最小の豊富さが0の場合は、値がゼロでないかどうかだけを確認します。

`AbstractAbundanceTable`に使用した場合、同じサイズのスパースブール行列を返します。
