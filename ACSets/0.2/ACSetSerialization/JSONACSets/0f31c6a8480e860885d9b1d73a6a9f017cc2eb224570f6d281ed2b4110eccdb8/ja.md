```julia
# JSON-able object representing an ACSet
acset = Dict(
    "type" => "ACSet",
    "elements" => [
        Dict("name" => "element1", "value" => 10),
        Dict("name" => "element2", "value" => 20)
    ],
    "metadata" => Dict(
        "created" => "2023-10-01",
        "updated" => "2023-10-02"
    )
)
```
