```
CostModel(submat, insertion, deletion)
CostModel(submat, insertion=, deletion=)
CostModel(match=, mismatch=, insertion=, deletion=)
```

Cost model.

This creates a cost model object for alignment from substitution matrix (`submat`), an insertion cost (`insertion`), and a deletion cost (`deletion`). Note that both of the insertion and deletion costs should be non-negative.  As a shorthand of creating a dichotomous substitution matrix, you can write as, for example, `CostModel(match=0, mismatch=1, insertion=2, deletion=2)`.

## Example

```
using BioAlignments

# create a cost model from a substitution matrix and indel costs
cost = CostModel(ones(128, 128) - eye(128), insertion=.5, deletion=.5)

# run global alignment to minimize edit distance
pairalign(EditDistance(), "intension", "execution", cost)
```

See also: `SubstitutionMatrix`, `pairalign`, `AffineGapScoreModel`
