```
feedback(sys)
feedback(sys1, sys2)
```

For a general LTI-system, `feedback` forms the negative feedback interconnection

```julia
>-+ sys1 +-->
  |      |
 (-)sys2 +
```

If no second system is given, negative identity feedback is assumed
