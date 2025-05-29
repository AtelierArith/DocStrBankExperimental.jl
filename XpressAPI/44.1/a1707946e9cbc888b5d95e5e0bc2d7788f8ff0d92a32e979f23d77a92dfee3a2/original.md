```
XPRS_SIFTPASSES
```

Determines how quickly we allow to grow the worker problems during the sifting algorithm. (integer)

Using larger values can increase the number of columns added to the worker problem which often results in increased solve times for the worker problems but the number of necessary sifting iterations may be reduced. .

Default value: `4`

Domain: 1~INF
