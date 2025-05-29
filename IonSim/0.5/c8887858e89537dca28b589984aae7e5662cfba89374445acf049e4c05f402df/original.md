```
transitionfrequency(I::Ion, transition::Tuple; B=0, ignore_manualshift=false)
```

`transition` is a Tuple of two sublevels or levels.

Computes the absolute values of the difference in energies between `transition[1]` and `transition[2]`.

If between sublevels, then the Zeeman shift may be included by setting the value of the magnetic field `B`, and manual shifts may be omitted by setting `ignore_manualshift=true`.
