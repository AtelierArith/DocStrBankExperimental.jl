```
Provenance(object, [sigtype=NoSignature()])
```

Captures and timestamps the provenance data associated with `object` as defined by the `provenance` definition for the type of `object`.

To be called by provenance tracking packages that want to capture provenance data associated with `object`. By passing in a `sigtype` the signing of the generated provenance data can be customized.
