```
create_decision_model(node::Node, tspan; node_strategy::DataStructures.OrderedDict, species::Type{<:Species}=AedesAegypti,do_binary::Bool=false, optimizer=nothing)
```

Build mathematical program. Problem created as an NLP (do*binary=false) or MINLP (do*binary=true). NB: `Node` is recreated as a `Network` object internally; this does not change the problem but is relevant for data exploration as it adds one index layer to the formatted results.
