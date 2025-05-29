```
dₘ = delaymargin(G::LTISystem)
```

Return the delay margin, dₘ. For discrete-time systems, the delay margin is normalized by the sample time, i.e., the value represents the margin in number of sample times.  Only supports SISO systems.
