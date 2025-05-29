```
ROC(pfa::Vector, pmiss::Vector, ch::BitArray, θ::Vector, llr::Vector)
```

Stores the essential performance information that can be extracted from a set of supervised trials, i.e., target and non-target scores from a two-class classifier.  Apart from the (minimalized) arrays for probabilities of false-alarm `pfa` and miss `pmiss`–-the coordinates of the ROC curve–-, they are the threshold `θ` for these, a boolean whether-or-not this point lies on the convex hull `ch`, and the associated optimal log-likelihood-ratio `llr` associated to the line segment.
