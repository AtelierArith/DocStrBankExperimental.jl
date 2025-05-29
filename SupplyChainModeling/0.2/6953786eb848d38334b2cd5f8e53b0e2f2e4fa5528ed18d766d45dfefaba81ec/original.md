```
add_product!(storage::Storage, product; initial_inventory::Real=0, 
                                        unit_handling_cost::Real=0,
                                        unit_holding_cost::Real=0, 
                                        maximum_throughput::Float64=Inf, 
                                        additional_stock_cover::Real=0.0)
```

Indicates that a storage can store a product.

The keyword arguments are:     - `initial_inventory`: the amount of product initially at the storage location     - `unit_handling_cost`: : the cost of handling a unit of product at the storage location     - `unit_holding_cost`: the cost of holding a unit of product at the storage location per period     - `maximum_throughput`: the maximum number of units of product that can be sent per period
