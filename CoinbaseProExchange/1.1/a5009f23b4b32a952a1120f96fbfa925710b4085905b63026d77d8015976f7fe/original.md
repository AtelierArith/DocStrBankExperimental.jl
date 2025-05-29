```
cancel_order(order_id::String, user_data::UserInfo)
```

Cancel an order with a given order ID.

# Arguments

  * `order_id::String` : Order ID, can be obtained via

`show_open_orders(user_data)`

  * `user_data::UserInfo` : API data

# Example

```julia-repl
julia>cancel_order("5591e17e-5f79-41f0-93d5-b455ec552ecc", user_data)
"5591e17e-5f79-41f0-93d5-b455ec552ecc"
```
