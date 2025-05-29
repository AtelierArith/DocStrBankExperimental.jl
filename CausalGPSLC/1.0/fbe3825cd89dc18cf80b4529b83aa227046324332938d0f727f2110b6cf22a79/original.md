Constructor for GPSLCObject that samples from the  posterior before constructing the GPSLCObject.

```
GPSLCObject(hyperparams, priorparams, SigmaU, obj, X, T, Y)
GPSLCObject(hyperparams, priorparams, SigmaU, obj, nothing, T, Y)
GPSLCObject(hyperparams, priorparams, nothing, nothing, X, T, Y)
GPSLCObject(hyperparams, priorparams, nothing, nothing, nothing, T, Y)
```

Full Model or model with no observed Covariates
