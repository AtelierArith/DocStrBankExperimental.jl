```
BottomHolePressureTarget(q, phase)
```

Bottom-hole pressure (bhp) target with target pressure value `bhp`. A well operating under a bhp constraint will keep the well pressure at the bottom hole (typically the top of the perforations) fixed at this value unless doing so would violate other constraints, like the well switching from injection to production when declared as an injector.

# Examples

```julia-repl
julia> BottomHolePressureTarget(100e5)
BottomHolePressureTarget with value 100.0 [bar]
```
