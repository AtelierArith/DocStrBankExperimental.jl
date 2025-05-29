```
NA(na=isnan)
```

Choose filtering using "NA" (Not Available) boundary conditions. This is most appropriate for filters that have only positive weights, such as blurring filters. Effectively, the output value is normalized in the following way:

```
          filtered array with Fill(0) boundary conditions
output =  -----------------------------------------------
          filtered 1     with Fill(0) boundary conditions
```

Array elements for which `na` returns `true` are also considered outside array boundaries.
