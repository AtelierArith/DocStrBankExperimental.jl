```
sc[st] = v
```

If `st` is a semitoken and `sc` is a SortedDict or SortedMultiDict, then `sc[st]` refers to the value field of the (key,value) pair that the full token `(sc,st)` refers to. This expression may occur on either side of an assignment statement. Time: O(1)
