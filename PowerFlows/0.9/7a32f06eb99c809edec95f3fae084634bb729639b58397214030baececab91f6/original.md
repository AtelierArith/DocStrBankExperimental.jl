Update the `PSSEExporter` with new `data`.

# Arguments:

  * `exporter::PSSEExporter`: the exporter to update
  * `data::PSY.System`: system containing the new data. Must be fundamentally the same

`System` as the one with which the exporter was constructed, just with different values —   this is the user's responsibility, we do not exhaustively verify it.
