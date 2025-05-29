```
create_decision_model(network::Network, tspan; node_strategy::DataStructures.OrderedDict, species::Type{<:Species}=AedesAegypti,do_binary::Bool=false, optimizer=nothing)
```

Build mathematical program. Problem created as an NLP (do*binary=false) or MINLP (do*binary=true).
