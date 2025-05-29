```
simulate_forward(eventHistory, maxT, startT, bg, kappa, kern)
```

Simulate a Hawkes process given we have already observed some events. This can be used to forecast future events. 

# Arguments

  * `eventHistory` The events that have ocured so far.
  * `maxT` Maximum time value to simulate forward to.
  * `startT` Starting time from which to simulate forward.
  * `bg` Background value
  * `kappa` Kappa value
  * `kern` Kernel function or distribution
