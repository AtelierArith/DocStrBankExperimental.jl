Creates a new order

https://docs.gemini.com/rest-api/#new-order

# Arguments:

  * `sandbox::Bool`: Sandbox request
  * `api_key::String`: Gemini API key
  * `api_secret::String`: Gemini API secret
  * `side::String`: "buy" or "sell"
  * `symbol::String`: The symbol for the new order
  * `amount::String`: Quoted decimal amount to purchase
  * `price::String`: Quoted decimal amount to spend per unit
  * `type::String`: The order type. "exchange limit" for all order types except for stop-limit orders. "exchange stop limit" for stop-limit orders.
  * `options::Vector{String}`:	Optional. An optional array containing at most one supported order execution option.
  * `stop_price::String`: Optional. The price to trigger a stop-limit order. Only available for stop-limit orders.
