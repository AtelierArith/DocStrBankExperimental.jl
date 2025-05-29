```
extrude(i)
```

The extrude protocol declares that the tensor update happens in order and only once, so that reduction loops occur below the extrude loop. It is not usually necessary to declare an extrude protocol, but it is used internally to reason about tensor format requirements.
