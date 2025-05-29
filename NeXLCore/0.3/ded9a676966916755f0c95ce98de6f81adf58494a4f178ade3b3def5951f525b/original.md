`NormalizeByShell` normalizes the sum of all the weights associated with a shell to unity. Example: 

```
sum(cxr=>weight(NormalizeByShell, cxr), characteristic(n"Fe", ltransitions))==1.0
```
