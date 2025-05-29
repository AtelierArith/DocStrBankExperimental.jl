```
gas_unit_converter(
    value_in::Unitful.Quantity,
    units_in::String,
    units_out::String;
    species::String="H",
    temperature=293.15 * Unitful.K,
)
```

Converts gas flows between different units. Uses ideal gas law to convert between Pressure * volume type flows / quantities and count / current types of units. This is the Unitful version.

Output will be unitful, but the units are not simplified automatically. You can perform operations such as

  * `(output |> Unitful.upreferred).val`
  * `Unitful.uconvert(Unitful.whatever, output).val`

to handle simplification or conversion of units.

Although this function pretends torr L s$^{-1}$ and Pa m$^3$ s$^{-1}$ are different, use of Unitful should cause them to behave the same way as long as you simplify or convert units at the end. This means that you can use other pressure*volume type gas units and call them torr L s$^{-1}$ and the script will deal with them up to having messy units in the output.
