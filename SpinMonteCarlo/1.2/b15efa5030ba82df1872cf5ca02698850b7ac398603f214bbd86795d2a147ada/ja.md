```
binning(obs::SimpleObservable; binsize::Int = 0, numbins::Int = 0)
binning(obs::SimpleVectorObservable; binsize::Int = 0, numbins::Int = 0)

観測可能な `obs` をビンに分けます。
`binsize` または `numbins` のいずれかを指定できます。両方が指定された場合、`ArgumentError` がスローされます。
両方が指定されていない場合、`binsize` は `floor(sqrt(count(obs)))` に設定されます。
```
