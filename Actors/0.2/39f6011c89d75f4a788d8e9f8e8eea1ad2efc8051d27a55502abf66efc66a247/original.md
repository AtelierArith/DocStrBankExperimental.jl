```
exit!(lk::Link, reason=:normal)
exit!(name::Symbol, ....)
```

Tell an actor `lk` (or `name` if registered) to stop. If it  has a [`term`](@ref _ACT) function, it calls that with  `reason` as last argument. 
