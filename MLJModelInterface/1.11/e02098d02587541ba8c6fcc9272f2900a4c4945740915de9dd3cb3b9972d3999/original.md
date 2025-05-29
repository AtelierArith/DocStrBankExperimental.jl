```
fitted_params(model, fitresult) -> human_readable_fitresult # named_tuple
```

Models may overload `fitted_params`. The fallback returns `(fitresult=fitresult,)`.

Other training-related outcomes should be returned in the `report` part of the tuple returned by `fit`.
