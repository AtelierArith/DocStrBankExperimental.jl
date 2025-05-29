```
AffineGapScoreModel(submat, gap_open, gap_extend)
AffineGapScoreModel(submat, gap_open=, gap_extend=)
AffineGapScoreModel(match=, mismatch=, gap_open=, gap_extend=)
```

Affine gap scoring model.

This creates an affine gap scroing model object for alignment from a substitution matrix (`submat`), a gap opening score (`gap_open`), and a gap extending score (`gap_extend`). A consecutive gap of length `k` has a score of `gap_open + gap_extend * k`. Note that both of the gap scores should be non-positive.  As a shorthand of creating a dichotomous substitution matrix, you can write as, for example, `AffineGapScoreModel(match=5, mismatch=-3, gap_open=-2, gap_extend=-1)`.

## Example

```
using BioSequences
using BioAlignments

# create an affine gap scoring model from a predefined substitution
# matrix and gap opening/extending scores.
affinegap = AffineGapScoreModel(BLOSUM62, gap_open=-10, gap_extend=-1)

# run global alignment between two amino acid sequenecs
pairalign(GlobalAlignment(), aa"IDGAAGQQL", aa"IDGATGQL", affinegap)
```

See also: `SubstitutionMatrix`, `pairalign`, `CostModel`
