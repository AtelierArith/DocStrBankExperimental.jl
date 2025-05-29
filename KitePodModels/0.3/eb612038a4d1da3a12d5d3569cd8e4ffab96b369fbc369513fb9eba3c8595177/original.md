```
init_kcu!(kcu::KCU, set::KiteUtils.Settings)
```

Inititalze the model of the kite control unit (KCU).  The actual and the set values of depower are initialized to set.depower_offset * 0.01, the actual and the set values of steering to zero. 
