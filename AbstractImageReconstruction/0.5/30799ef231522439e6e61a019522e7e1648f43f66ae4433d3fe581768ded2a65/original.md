```
LinkedPropertyListener(fn, target::RecoPlan, targetProp, source::RecoPlan, sourceProp)
```

Connect two properties of `RecoPlans`. Set `target.targetProp` to `fn(source.sourceProp)` whenever `source.sourceProp` changes and `target.targetProp` was not changed outside of the listener.  
