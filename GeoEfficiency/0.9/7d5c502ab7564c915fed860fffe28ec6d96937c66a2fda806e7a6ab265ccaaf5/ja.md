```
geoEff(detector::Detector = Detector(), aSource::Tuple{Point, Real, Real} = source())::Float64
```

`geoEff(::Detector, ::Point, ::Real, ::Real)`と同じですが、引数をタプル`aSource`でスプラットしています。

!!! note
    ディテクタもソースタプルも提供されない場合、またはソースタプルのみが提供されない場合、ユーザーに`console`を介してソース（およびディテクタ）を入力するように促します。

