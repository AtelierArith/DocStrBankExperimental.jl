```
jet_filtering(jet, clusterseq, filter) -> PseudoJet
```

Filters a jet to retain only the hardest subjets based on a specified radius and number.

# Arguments:

  * `jet::PseudoJet`: PseudoJet instance representing the jet to filter.
  * `clusterseq::ClusterSequence`: ClusterSequence containing jet history.
  * `filter::JetFilter`: Filter instance specifying radius and number of subjets.

# Returns:

  * `PseudoJet`: Filtered jet composed of the hardest subjets.
