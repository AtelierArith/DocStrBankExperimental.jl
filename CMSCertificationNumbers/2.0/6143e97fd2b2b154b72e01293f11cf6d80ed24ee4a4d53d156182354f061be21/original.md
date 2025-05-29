```
IPPSExcludedProviderCCN
IPPSExcludedProviderCCN(n::AbstractString)
```

A type representing a Medicare or Medicaid provider excluded from the Inpatient Prospective Payment System (IPPS).

IPPS-Excluded providers use six-character identifiers with the following format:

> `SSTAQQ`


Where:

  * `SS` represent a two-character alphanumeric State Code;
  * `T` represents an alphabetical Facility Type Code;
  * `A` represents either an alphabetical Parent Facility Type Code (for IPPS-Excluded units of IPPS-Excluded parent facilities) or the most significant digit of the Sequence Number;
  * `QQ` represents the two least significant digits of the Sequence Number.

!!! note
    IPPS-Excluded providers are always subunits of parent facilities, and as such they are not assigned their own CCN Sequence Number. The Sequence Number in the CCN will match the least significant digits of the parent facility.


The constructor performs no error checking, but will throw an exception if `n` has more than seven characters.
