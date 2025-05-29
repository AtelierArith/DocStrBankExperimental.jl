```
@datafunc function f(x::DT=>T, y::DS=>S...)
    ...
end
```

Define the function `f(x::T, y::S, ...)` and add data dispatch rules so that `f(x::DataSet, y::DataSet)` will open datasets matching dataset types `DT,DS` as Julia types `T,S`.
