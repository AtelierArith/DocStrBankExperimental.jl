```
mass_drop(jet, clusterseq, tag) -> PseudoJet
```

Identifies subjets in a jet that pass the mass drop tagging condition. The method stops at the first jet satisfying the mass and distance thresholds.

# Arguments:

  * `jet::PseudoJet`: PseudoJet instance representing the jet to tag.
  * `clusterseq::ClusterSequence`: ClusterSequence with jet clustering history.
  * `tag::MassDropTagger`: MassDropTagger instance providing mass drop parameters.

# Returns:

  * `PseudoJet`: The jet (or subjet) satisfying the mass drop conditions, if tagging is successful, otherwise a zero-momentum PseudoJet
