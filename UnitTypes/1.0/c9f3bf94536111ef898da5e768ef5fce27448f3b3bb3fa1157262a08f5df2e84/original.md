`macro relateMeasures(relation)`

Adds a multiplicative relationship between the left and right sides of the equation, allowing units to be multiplied and divided with consistent units.   All types must already be defined and only one * is supported on the left side, while the right should the resultant type.

`@relateMeasures Meter*Newton = NewtonMeter`
