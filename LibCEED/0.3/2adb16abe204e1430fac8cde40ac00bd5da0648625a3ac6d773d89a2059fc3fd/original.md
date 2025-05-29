```
apply!(op::Operator, vin, vout; request=RequestImmediate())
```

Apply the action of the operator `op` to the input vector `vin`, and store the result in the output vector `vout`.

For non-blocking application, the user can specify a request object. By default, immediate (synchronous) completion is requested.
