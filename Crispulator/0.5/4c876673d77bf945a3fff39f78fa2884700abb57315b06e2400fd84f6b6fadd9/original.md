```julia
auprc(scores, classes, pos_labels; rev)

```

Computes the area under the Precision-Recall curve using a lower trapezoidal estimator, which is more accurate for skewed datasets.

K. Boyd, K. H. Eng, and C. D. Page, “Area under the Precision-Recall Curve: Point Estimates and Confidence Intervals,” in Machine Learning and Knowledge Discovery in Databases, H. Blockeel, K. Kersting, S. Nijssen, and F. Železný, Eds. Springer Berlin Heidelberg, 2013, pp. 451–466.
