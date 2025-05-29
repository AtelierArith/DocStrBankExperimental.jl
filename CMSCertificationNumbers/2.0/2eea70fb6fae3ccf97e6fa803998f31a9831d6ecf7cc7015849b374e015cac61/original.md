```
EmergencyHospitalCCN
EmergencyHospitalCCN(n::AbstractString)
```

A type representing a designated Emergency Hospital provider.

Emergency Hospital providers use six-character identifiers with the following format:

> `SSQQQE`


Where:

  * `SS` represent a two-character alphanumeric State Code;
  * `E` represents an alphabetical Emergency Hospital Type Code;
  * `QQQ` represents a three-digit Sequence Number.

The constructor performs no error checking, but will throw an exception if `n` has more than seven characters.
