```
pairalign(type, seq, ref, model, [options...])
```

Run pairwise alignment between two sequences: `seq` and `ref`.

Available `type`s are:

  * `GlobalAlignment()`
  * `LocalAlignment()`
  * `SemiGlobalAlignment()`
  * `OverlapAlignment()`
  * `EditDistance()`
  * `LevenshteinDistance()`
  * `HammingDistance()`

`GlobalAlignment`, `LocalAlignment`, `SemiGlobalAlignment`, and `OverlapAlignment` are problem that maximizes alignment score between two sequences.  Therefore, `model` should be an instance of `AbstractScoreModel` (e.g. `AffineGapScoreModel`).

`EditDistance`, `LevenshteinDistance`, and `HammingDistance` are problem that minimizes alignment cost between two sequences.  As for `EditDistance`, `model` should be an instance of `AbstractCostModel` (e.g. `CostModel`). `LevenshteinDistance` and `HammingDistance` have predefined a cost model, so users cannot specify a cost model for these alignment types.

When you pass the `score_only=true` or `distance_only=true` option to `pairalign`, the result of pairwise alignment holds alignment score/distance only.  This may enable some algorithms to run faster than calculating full alignment result.  Other available `options` are documented for each alignemnt type.

## Example

```
using BioSequences
using BioAlignments

# create affine gap scoring model
affinegap = AffineGapScoreModel(
    match=5,
    mismatch=-4,
    gap_open=-5,
    gap_extend=-3
)

# run global alignment between two DNA sequences
pairalign(GlobalAlignment(), dna"AGGTAG", dna"ATTG", affinegap)

# run local alignment between two DNA sequences
pairalign(LocalAlignment(), dna"AGGTAG", dna"ATTG", affinegap)

# you cannot specify a cost model in LevenshteinDistance
pairalign(LevenshteinDistance(), dna"AGGTAG", dna"ATTG")
```

See also: `AffineGapScoreModel`, `CostModel`
