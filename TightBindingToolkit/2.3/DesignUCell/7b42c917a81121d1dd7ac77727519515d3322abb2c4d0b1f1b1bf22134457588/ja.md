```julia
ScaleBonds!(uc::UnitCell, dist::Float64, scale::Number)
ScaleBonds!(uc::UnitCell, label::String, scale::Number)
```

指定されたスケーリングファクターで、`UnitCell`内の既存の結合の行列を、与えられた`label`または指定された距離=`dist`でスケーリングします。
