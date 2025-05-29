```
computed_highest_diff_variables(structure)
```

Computes which variables are the "highest-differentiated" for purposes of pantelides. Ordinarily this is relatively straightforward. However, in our case, there is one complicating condition:

```
We allow variables in the structure graph that don't appear in the
system at all. What we are interested in is the highest-differentiated
variable that actually appears in the system.
```

This function takes care of these complications are returns a boolean array for every variable, indicating whether it is considered "highest-differentiated".
