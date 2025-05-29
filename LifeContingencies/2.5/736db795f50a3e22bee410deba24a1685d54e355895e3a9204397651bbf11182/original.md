```
present_value(Insurance,`time`)
```

The actuarial present value of the given insurance benefits, as if you were standing at `time`. 

For example, if the given `Insurance` has *decremented* payments `[1,2,3,4,5]` at times `[1,2,3,4,5]` and you call `pv(ins,3)`,  you will get the present value of the payments `[4,5]` at times `[1,2]`.

To get an undecremented present value, divide by the survivorship to that timepoint:

```julia
present_value(ins,10) / survival(ins,10)
```
