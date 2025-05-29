```
jet_trimming(jet, clusterseq, trim) -> PseudoJet
```

Trims a jet by removing subjets with transverse momentum below a specified fraction.

# Arguments:

  * `jet::PseudoJet`: PseudoJet instance representing the jet to trim.
  * `clusterseq::ClusterSequence`: ClusterSequence containing jet history.
  * `trim::JetTrim`: Trim instance specifying trimming parameters.

# Returns:

  * `PseudoJet`: Trimmed jet composed of retained subjets.
