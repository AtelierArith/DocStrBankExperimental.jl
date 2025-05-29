```
AUC
```

ROC curve and area under the ROC curve (AUC) are generally used in evaluation of the classification problems, but these concepts can also be interpreted in a context of ranking problem. Basically, the AUC metric for ranking considers all possible pairs of truth and other items which are respectively denoted by $i^+ \in \mathcal{I}^+_u$ and $i^- \in \mathcal{I}^-_u$, and it expects that the $best'' recommender completely ranks$i^+$higher than$i^-``, as follows:

![auc](./assets/images/auc.png)

AUC calculation keeps track the number of true positives at different rank in $\mathcal{I}$. At line 8, the function adds the number of true positives which were ranked higher than the current non-truth sample to the accumulated count of correct pairs. Ultimately, an AUC score is computed as portion of the correct ordered $(i^+, i^-)$ pairs in the all possible combinations determined by $|\mathcal{I}^+_u| \times |\mathcal{I}^-_u|$ in set notation.

```
measure(
    metric::AUC,
    truth::AbstractVector{T},
    pred::AbstractVector{T}
)
```
