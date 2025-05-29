```
const ELEMENTS
```

Constants related to elements. It is a dictionary with five keys

  * `:MW`: atomic weights.
  * `:ABUNDANCE`: natrural abundance.
  * `:ISOTOPES`: possible isotopes.
  * `:PARENTS`: parent element.
  * `:DECODES`: decode encoded string for `parse_compound`.

# The Most Common Elements (Parent Elements)

C, H, O, N, P, S, Li, Na, K, F, Cl, Ag 

# Minor Isotopes

[13C], [2H](D), [17O], [18O], [15N], [33S], [34S], [35S], [6Li], [40K], [41K], [37Cl], [109Ag]

By default, parent elements are considered possibly replaced by minor isotopes except that in `parent` chemical of `Isotopomers`, the number of replacement is restricted by field `isotopes`. On the other hand, minor elements are fixed.  
