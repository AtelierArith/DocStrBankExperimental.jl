`macro makeBaseMeasure(quantityName, unitName, unitSymbol::String, isAffine=false)`

Make a new base measure which has no relationship to an existing unit.   For example, in `@makeBaseMeasure Length Meter "m"`:

  * `quantityName` is the name of the measure, 'Length' above.
  * `unitName` is the name of the unit which will be used to make measures bearing that unit, 'Meter' above.
  * `unitSymbol` is the abbreviation of the unit name, used in all string presentations of the measure.
  * `isAffine` is normally false, if true the +-/* operations are not added for this and derived units and need to be added by hand.

The macro will introduce `AbstractLength <: AbstractMeasure` and `Meter()` into the current scope.

Measures created by the macro have fields:

  * `value::Number` raw value of the measure
  * `toBase::Number` == 1 for base measures
  * `unit::String` the unit to be displayed

To get the measure's value in the base unit as a float, see toBaseFloat().
