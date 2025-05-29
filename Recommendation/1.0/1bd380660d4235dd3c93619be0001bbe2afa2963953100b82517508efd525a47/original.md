```
SyntheticRule{probability::Float64[, item::Union{Nothing, Integer}, match::Function])
```

Matching rule for cumulative "click through rate". Given an item index, we increase the probability of acceptance upon sampling when `match` returns `true`, which takes a dictionary of feature name => value.

```julia
rules = SyntheticRule[]

push!(rules, SyntheticRule(0.001))
push!(rules, SyntheticRule(0.01, 3))
push!(rules, SyntheticRule(0.30, 1, s -> s["Age"] >= 1980 && s["Age"] <= 1989 && s["Geo"] == "New York"))
push!(rules, SyntheticRule(0.30, 2, s -> s["Age"] >= 1950 && s["Age"] <= 1959 && s["Geo"] == "New York"))
push!(rules, SyntheticRule(0.30, 2, s -> s["Age"] >= 1980 && s["Age"] <= 1989 && s["Geo"] == "Arizona"))
push!(rules, SyntheticRule(0.30, 1, s -> s["Age"] >= 1950 && s["Age"] <= 1959 && s["Geo"] == "Arizona"))
```
