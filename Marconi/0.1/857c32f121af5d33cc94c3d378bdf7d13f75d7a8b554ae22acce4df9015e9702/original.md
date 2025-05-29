```
cascade(net1,net2,net3,...,netN)
```

Returns a new `DataNetwork` that is the cascaded result of net1,net2,net3,...netN where the `nets` are a mixture of 2-Port `DataNetwork` objects and 2-Port `EquaionNetwork` object. Optionally takes kwarg `numpoints` for how many points in the result.

See the docs for details of dealing with equation-driven networks
