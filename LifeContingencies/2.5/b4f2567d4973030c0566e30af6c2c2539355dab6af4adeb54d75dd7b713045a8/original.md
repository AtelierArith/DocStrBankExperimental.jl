```
survival(lc::LifeContingency,from_time,to_time)
survival(lc::LifeContingency,to_time)
```

Return the probability of survival for the given LifeContingency, with decrements beginning at time zero. 

# Examples

```julia-repl julia> q = [.1,.2,.3,.4];

julia> l = SingleLife(mortality=q);

julia> survival(l,1) 0.9

julia> decrement(l,1) 0.09999999999999998

julia> survival(l,1,2) 0.8

julia> decrement(l,1,2) 0.19999999999999996

julia> survival(l,1,3) 0.5599999999999999

julia> decrement(l,1,3) 0.44000000000000006

````
```
````
