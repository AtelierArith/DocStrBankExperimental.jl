```
left_virtualspace(ψ::AbstractMPS, [pos=1:length(ψ)])
```

Return the virtual space of the bond to the left of sites `pos`.

!!! warning
    In rare cases, the gauge tensor on the virtual space might not be square, and as a result it cannot always be guaranteed that `right_virtualspace(ψ, i - 1) == left_virtualspace(ψ, i)`

