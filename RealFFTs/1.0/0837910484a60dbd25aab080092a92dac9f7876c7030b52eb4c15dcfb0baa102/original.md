```
plan = plan_rfft!(RC::RCpair; flags=FFTW.ESTIMATE, timelimit=FFTW.NO_TIMELIMIT)
```

Create a plan for performing the real-to-complex FFT on the data in `RC`. Perform the FFT with `plan(RC)`.

Planning allows you to optimize the performance of (I)FFTs for particular sizes of arrays. See the FFTW documentation for more information about planning.
