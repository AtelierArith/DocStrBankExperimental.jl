```
bandgap(job::Job, nelec=nothing)
```

Calculates the bandgap (possibly indirect) around the fermi level. Uses the first found bands calculation, if there is none it uses the first found nscf calculation.
