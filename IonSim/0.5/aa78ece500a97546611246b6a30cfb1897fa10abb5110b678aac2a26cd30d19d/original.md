```
energy(I::Ion, sublevel; B=0, ignore_manualshift=false)
```

Returns energy of `sublevel` of `I`. A Zeeman shift may be included by setting the value of the magnetic field `B`. The manual shift may be omitted by setting `ignore_manualshift=true`.
