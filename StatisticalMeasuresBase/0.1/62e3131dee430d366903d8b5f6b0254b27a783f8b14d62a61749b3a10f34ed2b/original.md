```
@trait SomeMeasureType trait1=value1 trait2=value2 ...
```

Declare `SomeMeasureType` a type whose instances are measures, and overload the specified traits to have the given values on all such instances.

For example, if `AUC` is a type, then

```
@trait AUC orientation = Loss() supports_weights = true
```

is equivalent to the declarations

```
StatisticalMeasuresBase.is_measure(::AUC) = true
StatisticalMeasuresBase.orientation(::AUC) = Score()
StatisticalMeasuresBase.supports_weights(::AUC) = true
```
