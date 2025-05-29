```
==(K::KodairaSymbol, s::String) -> Bool
```

Return true if K is corresponds to the Kodaira symbol given by the string. Valid inputs are : I0, II, III, IV and In where n is a positive integer, I0*, II*, III*, IV* and In* where n is a positive integer.

Instead of substituting n for an integer one may also check against the generic types 'In' or 'In*' to test if the Kodaira symbol is of that type.
