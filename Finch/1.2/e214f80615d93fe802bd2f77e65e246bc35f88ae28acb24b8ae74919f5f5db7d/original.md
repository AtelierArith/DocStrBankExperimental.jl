```
postype(lvl)
```

Return a position type with the same flavor as those used to store the positions of the fibers contained in `lvl`. The name position descends from the pos or position or pointer arrays found in many definitions of CSR or CSC. In Finch, positions should be data used to access either a subfiber or some other similar auxiliary data. Thus, we often end up iterating over positions.
