evaluateclustering(clusts::ClustLabelVector, truth::ClustLabelVector) Returns a named tuple of values quantifying the accuracy of the clustering assignments in `clusts` with respect to the ground truth clustering assignments in `truth`.

# Return values

  * `nbloss`: Normalised Binder loss (= 1 - rand index). Lower is better.
  * `ari`: Adjusted Rand index. Higher is better.
  * `vi`: Variation of Information distance ($\in [0, \log N]$). Lower is better.
  * `nvi`: Normalised VI distance ($\in [0, 1]$).
  * `id`: Information Distance ($\in [0, \log N]$). Lower is better.
  * `nid`: Normalised Information Distance ($\in [0, 1]$).
  * `nmi`: Normalised Mutual Information ($\in [0, 1]$). Higher is better.
