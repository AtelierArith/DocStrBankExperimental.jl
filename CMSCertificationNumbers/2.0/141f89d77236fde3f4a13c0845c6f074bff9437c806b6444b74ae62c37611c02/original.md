```
SupplierCCN
SupplierCCN(n::AbstractString)
```

A type representing a Medicare or Medicaid Supplier.

Suppliers use ten-character identifiers with the following format:

> `SSTQQQQQQQ`


Where:

  * `SS` represent a two-character alphanumeric State Code;
  * `T` represents a Supplier Type Code;
  * `QQQQQQQ` represents a seven-digit Sequence Number.

The constructor performs no error checking, but will throw an exception if `n` has more than 15 characters.
