```
LinearConstraint{S,P,W,T}
```

Linear constraint of the form $Ay - b \{\leq,=\} 0$ where $y$ may be either the state or controls (but not a combination of both).

# Constructor: ```julia

LinearConstraint{S,W}(n,m,A,b) ```where`W <: Union{State,Control}`.
