# RPTreeEvent

Event on Node of Tree We store the event as it enables propagating a new data across the tree if we want to do any learning

FIELDS

. split : the split event coded as constants `splitDiam` or `splitProj` or `splitNull` . diameters : a vector of size 2 containing mean diameter and then max diameter . projEvent  field of struct Union{RPTProjParams, Nothing} . diamEvent  field of struct Union{RPTDiamSplit, Nothing}

METHODS

```
1. `function RPTreeEvent(s::Int64, diameters::Vector{Float64}, pivot::Union{RPTDiamSplit,Nothing})`
constructor for split on diameter criteria

2. `function RPTreeEvent(s::Int64, diameters::Vector{Float64}, projData::Union{RPTProjParams, Nothing})`
    constructor for split on projection against a random Vector
    as diameters are always estimated (the struct of split depends upon computed diameters),
    they always are in the constructor

3. `function RPTreeEvent(diameters::Vector{Float64})`
     a constructor used to just store diameter estimation at leaves. Used with event splitNull
```
