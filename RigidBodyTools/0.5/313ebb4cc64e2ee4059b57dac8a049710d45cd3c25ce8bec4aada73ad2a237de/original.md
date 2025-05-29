```
getrange(ls::RigidBodyMotion,dimfcn::Function,jid::Int) -> Range
```

Return the subrange of indices in the global state vector for the state corresponding to joint `jid` in linked system `ls`.
