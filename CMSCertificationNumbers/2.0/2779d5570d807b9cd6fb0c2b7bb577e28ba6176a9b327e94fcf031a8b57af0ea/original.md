```
MedicareProviderCCN
MedicareProviderCCN(n::AbstractString)
```

A type representing a Medicare provider.

Medicare providers use six-character identifiers with the following format:

> `SSPQQQ`


Where:

  * `SS` represent a two-character alphanumeric State Code;
  * `P` represents either an a literal 'P' character (for Organ Procurement Organizations) or the most significant digit of the Sequence Number;
  * `QQQ` represents the three least significant digits of the Sequence Number.

The constructor performs no error checking, but will throw an exception if `n` has more than seven characters.
