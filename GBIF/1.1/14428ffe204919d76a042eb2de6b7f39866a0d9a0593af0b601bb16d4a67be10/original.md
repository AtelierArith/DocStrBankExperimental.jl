**Represents an occurrence in the GBIF format**

This is currently a subset of all the fields. This `struct` is *not* mutable – this ensures that the objects returned from the GBIF database are never modified by the user.

The `taxon` field is a `GBIFTaxon` object, and can therefore be manipulated as any other `GBIFTaxon`.
