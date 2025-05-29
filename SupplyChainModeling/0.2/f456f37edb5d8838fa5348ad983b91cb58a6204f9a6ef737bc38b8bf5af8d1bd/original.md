```
add_product!(plant::Plant, product::Product; bill_of_material::Dict{Product, Float64}, unit_cost, maximum_throughput)
```

Indicates that a plant can produce a product.

The keyword arguments are:

  * `bill_of_material`: the amount of other product needed to produce one unit of the product. This dictionary can be empty if there are no other products needed.
  * `unit_cost`: the cost of producing one unit of product.
  * `maximum_throughput`: the maximum amount of product that can be produced in a time period.
  * `time`: the production lead time.
