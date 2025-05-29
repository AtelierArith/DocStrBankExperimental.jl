```
add_product!(supplier::Supplier, product::Product; unit_cost::Float64, maximum_throughput::Float64)
```

Indicates that a supplier can provide a product.

The keyword arguments are:

  * `unit_cost`: the cost per unit of the product from this supplier.
  * `maximum_throughput`: the maximum number of units that can be provided in each time period.
