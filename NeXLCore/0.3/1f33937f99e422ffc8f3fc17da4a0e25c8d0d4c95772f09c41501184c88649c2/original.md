`NormalizeBySubShell` normalizes the sum of all the weights associated with a sub-shell to unity.

Example: 

```
sum(cxr=>weight(NormalizeBySubShell, cxr), characteristic(n"Fe", ltransitions))==1.0+1.0+1.0
```
