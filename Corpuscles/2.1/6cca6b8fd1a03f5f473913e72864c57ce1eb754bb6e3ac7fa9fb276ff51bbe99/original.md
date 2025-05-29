PDG IDs consist of 7 digits prefixed by a sign, following the scheme:

```
+/- N Nr Nl Nq1 Nq2 Nq3 Nj
```

Those are accessible as fields. There are PDG IDs with more than 7 digits for non-standard particles such as Q-balls. To support those, we follow the implementation in the SciKit-HEP `particle` Python package, which introduced N8, N9 and N10.
