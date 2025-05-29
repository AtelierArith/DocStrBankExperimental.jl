Base package for provenance providers and consumers.

Main extensions points are:

  * `provenance`: to be extended by "providers" of provenance data, i.e. packages with types that wish to provide provenance data about themselves.
  * `signature`: to be extended by "consumers" of provenance data, i.e. packages which capture, track, or analyse provenance data.

For details about extending these please see their respective documentation strings.
