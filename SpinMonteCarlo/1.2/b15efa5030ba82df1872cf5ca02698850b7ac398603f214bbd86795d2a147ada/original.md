```
binning(obs::SimpleObservable; binsize::Int = 0, numbins::Int = 0)
binning(obs::SimpleVectorObservable; binsize::Int = 0, numbins::Int = 0)

Binning the observable `obs`.
Either `binsize` or `numbins` can be given. If both are given, `ArgumentError` is thrown.
If both are not given, `binsize` is set to `floor(sqrt(count(obs)))`.
```
