```
condition(param::SymbolOrString, iftrue, iffalse; empty=nothing)
condition_test(test::String, iftrue, iffalse)
condition(param_then_pairs::Vector{Pair}, iffalse; empty::Vector=nothing)
condition_test(ifthen_pairs::Vector{Pair}, iffalse)
```

If iftrue/iffalse isn't a NamedTuple, then it'll be converted as a NamedTuple with name :value. Nested conditions via a vector of ifthen_pairs.

# Examples

```
condition(:myparam, 1, 2; empty=true)
condition_test("datum.x > 0", field("color:O"), :blue)
condition_test(["datum.x > 5" => field("color:O"), "datum.x < 0" => :blue], :gray)
```
