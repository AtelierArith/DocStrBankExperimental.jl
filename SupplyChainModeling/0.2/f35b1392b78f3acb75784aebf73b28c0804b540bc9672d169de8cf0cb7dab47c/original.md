```
add_demand!(supply_chain, customer, product, demand::Array{Float64, 1}; service_level=1.0)
```

Adds customer demand for a product. The demand is specified for each time period.

The keyword arguments are:

  * `service_level`: indicates how many lost sales are allowed as a ratio of demand. No demand can be lost if the service level is 1.0 and all demand can be lost if the service level is 0.0.
  * `sales_price`: the sales price of a unit of product.
  * `lost_sales_cost`: the cost of losing the sales of a unit of product.
