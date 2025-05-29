```
soft_drop(jet, clusterseq, tag) -> PseudoJet
```

Applies soft-drop grooming to remove soft, wide-angle radiation from jets. This function reclusters the jet and iteratively checks the soft-drop condition on subjets.

# Arguments:

  * `jet::PseudoJet`: PseudoJet instance to groom.
  * `clusterseq::ClusterSequence`: ClusterSequence containing jet history.
  * `tag::SoftDropTagger`: SoftDropTagger instance with soft-drop parameters.

# Returns:

  * `PseudoJet`: Groomed jet or zero-momentum PseudoJet if grooming fails.
