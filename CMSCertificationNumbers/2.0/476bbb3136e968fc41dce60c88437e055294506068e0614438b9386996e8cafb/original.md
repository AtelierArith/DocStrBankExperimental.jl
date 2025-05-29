```
MedicaidOnlyProviderCCN
MedicaidOnlyProviderCCN(n::AbstractString)
```

A type representing a Medicaid-Only provider.

Medicid-Only providers use six-character identifiers with the following format:

> `SSTQQQ`


Where:

  * `SS` represent a two-character alphanumeric State Code;
  * `T` represents an alphabetical Facility Type Code;
  * `QQQ` represents a three-digit Sequence Number.

The constructor performs no error checking, but will throw an exception if `n` has more than seven characters.
