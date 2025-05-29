```
JLLBuildInfo
```

A structure representing all platform-specific information in a JLL.  This structure is essentially a distillation of the `BuildResult/ExtractResult` structures in `BinaryBuilder2`, but is distinct in order to maintain separation between the two packages, and to make it easier for non-BinaryBuilder2 users to make use of this package if needed.
