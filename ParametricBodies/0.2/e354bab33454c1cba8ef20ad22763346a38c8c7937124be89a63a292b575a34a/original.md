```
update!(l::HashedLocator,curve,t,samples=l.lims)
```

Updates `l.hash` for `curve` at time `t` by searching through `samples` and refining.
