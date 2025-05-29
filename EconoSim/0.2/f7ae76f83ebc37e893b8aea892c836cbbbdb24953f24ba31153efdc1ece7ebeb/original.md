```
process_needs(needs::Needs
            type::NeedType,
            posessions::Entities = Entities())
```

Get a vector of all the needs of the actor of the specified need type. The vector contains named tuples {blueprint::Blueprint, units::Int}. If the need type is prioritised the list is in order of priority, otherwise it is randomized.
