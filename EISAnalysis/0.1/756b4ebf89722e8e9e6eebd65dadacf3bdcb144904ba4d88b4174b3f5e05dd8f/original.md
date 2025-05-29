```
circuit_fit(circuit, ω_data,Z_data)
```

Main function for fitting a Circuit to EIS data.

The initial guess is passed implicitly through the circuit definition. E.g.     randles_circuit = 0.23r-(r-0.025wo^80)/0.2c     # p0 = [0.23,1.0,(0.025,80),0.2]

# Attributes

  * `circuit`: Circuit for fitting
  * `ω_data`: EIS frequencies
  * `Z_data`: EIS impedance
