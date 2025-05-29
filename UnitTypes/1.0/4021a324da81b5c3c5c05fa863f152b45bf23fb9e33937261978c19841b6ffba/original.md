`macro makeMeasure(relation, unit="NoUnit", defineConverts=true)`

Creates a new Measure from an existing base measure.   The left hand side of the equation must already exist, while the right hand side should be undefined, with the trailing string providing the unit symbol.

`@makeMeasure Meter(1) = MilliMeter(1000) "mm"`

The resulting types are defined in the containing module, not in UnitTypes, as seen by `println(names(MyModule, all=true))`.
