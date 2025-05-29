```
JLLBuildLicense
```

Describes the license a JLL build is released under.  Contains a `filename`, and the full `license_text`, which gets written out to `${jll_prefix}/licenses/${filename}`. The `license_type` is the SPDX identifier of the license, if any exists.  This can be automatically determined by a convenience constructor, using `LicenseCheck`.
