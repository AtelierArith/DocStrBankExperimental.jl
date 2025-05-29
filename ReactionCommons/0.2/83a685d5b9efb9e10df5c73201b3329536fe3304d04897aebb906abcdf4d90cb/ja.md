反応のカバレッジ依存性、順序依存性、およびMWCを決定する関数

# 使用法

```
get_dependencies(cov_dep_rxns,order_dep_rxns,mwc_rxns,rxn_id)
```

  * cov*dep*rxns::Dict{Int64=>Dict{Int64=>Float64}}
  * order*dep*rxns::Dict{Int64=>Dict{Int64=>Float64}}
  * mwc_rxns::Array{Int64}
  * rxn_id::Int64

この関数は、cov、order、およびmwcのタプルを返します。
