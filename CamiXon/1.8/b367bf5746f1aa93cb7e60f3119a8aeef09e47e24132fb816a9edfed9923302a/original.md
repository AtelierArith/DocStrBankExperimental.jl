```
castElement(;Z=1, msg=true)
castElement(elt::String; msg=true)
```

Create Atom with fields

  * `.name`:  name of element
  * `.symbol`:  symbol of element
  * `.weight`:  relative atomic mass (atomic weight)

    `Z`: atomic number (nuclear charge number)

`elt`: symbolic element name

#### Example:

```
julia> castElement("Rb"; msg=false) == castElement(Z=37, msg=false)
true

julia> element = castElement(;Z=1, msg=true);
Element created: H, hydrogen, Z=1, weight=1.008

julia> element = castElement(;Z=1, msg=false)
Element("hydrogen", "H", 1.008)
```
