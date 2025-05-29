```
open_subscription(fn::Function,
                  [client::Client],
                  subscription_name::Union{Alias, AbstractString},
                  output_type::Type=Any;
                  sub_args=Dict(),
                  output_fields=String[],
                  initfn=nothing,
                  retry=true,
                  subtimeout=0,
                  stopfn=nothing,
                  throw_on_execution_error=false)
```

Subscribe to `subscription_name`, running `fn` on each received result and ending the subcription when `fn` returns `true`.

By default `fn` receives a `GQLReponse{Any}`, where the data for an individual result object can be found by `gql_response.data[subscription_name]`.

If used, `initfn` is called once the subscription is open.

The subscription uses the `ws_endpoint` field of the `client.`

This function is designed to be used with the `do` keyword.

# Arguments

  * `fn::Function`: function to be run on each result, recieves the response from the   subscription`. Must return a boolean to indicate whether or not to close the subscription,   with`true` closing the subscription.
  * `client::Client`: GraphQL client (optional). If not supplied, [`global_graphql_client`](@ref) is used.
  * `subscription_name::Union{Alias, AbstractString}`: name of subscription in server.
  * `output_type::Type=Any`: output data type for subscription response object. An object   of type `GQLResponse{output_type}` will be returned.For further information, see   documentation for `GQLResponse`.

# Keyword Arguments

  * `sub_args=Dict()`: dictionary of subscription argument key value pairs - can be   nested with dictionaries and vectors.
  * `output_fields=String[]`: output fields to be returned. Can be a string, or   composed of dictionaries and vectors.
  * `initfn=nothing`: optional function to be run once subscription is itialised.
  * `retry=true`: retry if subscription fails to open.
  * `subtimeout=0`: if `stopfn` supplied, this is the period that it is called at.   If `stopfn` is not supplied, this is the timeout for waiting for data. The timer   is reset after every subscription result is received.
  * `stopfn=nothing`: a function to be called every `subtimeout` that stops the   subscription if it returns positive. The timer is reset after every subscription   result is received.
  * `throw_on_execution_error=false`: set to `true` to stop an error being thrown if the GraphQL server   response contains errors that occurred during execution.
  * `verbose=0`: set to 1, 2 for extra logging.

# Examples

```julia
julia> open_subscription("subSaveUser", sub_args=Dict("role" => "SYSTEM_ADMIN")) do result
           fn(result)
       end
```

See also: [`GQLResponse`](@ref)
