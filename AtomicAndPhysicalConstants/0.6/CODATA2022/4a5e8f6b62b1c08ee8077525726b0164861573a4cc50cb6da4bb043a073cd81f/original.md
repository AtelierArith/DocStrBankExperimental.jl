```
@APCdef(unitsystem = ACCELERATOR, unittype = Float, name = :APC)
```

## Description:

It defines the physical constants and getter functions for species mass and charge with the proper unit and data.

## keyword parameters:

  * `unitsystem`   – type: 5-Tuple of `Unitful` units. Specify the unit system, default to `ACCELERATOR`, which sets units to 'Default units' (see below).                                       The other options are `MKS`, and `CGS`. It provides a convient way to set all the units.
  * `unittype`     – Sets the return type of the constants and the getter functions. It can be `Float`, `Unitful`, or `DynamicQuantities`. Default to `Float`.
  * `name`         – Sets the name of the module that contains the constants and getter functions. Default to `APC`.

## Note

  * @APCdef can be called only once in a module.

## Default units:

  * `mass`: eV/c^2
  * `length`: m
  * `time`: s
  * `energy`: eV
  * `charge`: elementary charge
