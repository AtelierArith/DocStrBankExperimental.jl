```
vmeasure_homogeneity_completeness(labels_true, labels_pred; β=1.)
```

calculates and returns v-measure, homogeneity, completeness; similar to f-score, precision, and recall respectively

Args:

  * β, weighting term for v-measure, if β is greater than 1 completeness

is weighted more strongly in the calculation, if β is less than 1,  homogeneity is weighted more strongly

Citation:

  * A. Rosenberg, J. Hirschberg, in Proceedings of the 2007 Joint Conference

on Empirical Methods in Natural Language Processing and Computational Natural  Language Learning (EMNLP-CoNLL) (Association for Computational Linguistics,   Prague, Czech Republic, 2007; https://aclanthology.org/D07-1043), pp. 410–420.
