```
Organ(f = [0.53, 0.25, 0.05, 0.05, 0.06, 0.06],
      te = 100.0, tm = 50.0, tb = 10.0, wmax = 0.1)
```

Data structure to store all parameters for the growth model of a plant organ.

# Arguments

  * `f`: fraction of dry matter allocated to different carbon pools of newly formed material, [carbohydrates, proteins, lipids, lignin, organic acids, minerals]
  * `te`: time at which growth rate extinguishes, [DD]
  * `tm`: time at which growth rate is maximum, [DD]
  * `tb`: base temperature, [°C]
  * `wmax`: maximum weight, [g]
