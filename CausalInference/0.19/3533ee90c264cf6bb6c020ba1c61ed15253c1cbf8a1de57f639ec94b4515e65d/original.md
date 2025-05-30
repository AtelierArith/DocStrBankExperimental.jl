```
kl_mutual_information(x, y; k=5, bias_correction=true)
```

compute the nearest-neighbor 'KGS' estimate of the mutual information between x and y.

x and y are 2d arrays, with every column representing one data point.  For further information, see

"Estimating Mutual Information" Alexander Kraskov, Harald Stoegbauer, and Peter Grassberger Physical Review E https://arxiv.org/pdf/cond-mat/0305641.pdf

"Demystifying Fixed k-Nearest Neighbor Information Estimators" Weihao Gao, Sewoong Oh, Pramod Viswanath EEE International Symposium on Information Theory - Proceedings https://arxiv.org/pdf/1604.03006.pdf

keyword arguments: k=5: number of nearest neighbors bias_correction=true: flag to apply Gao's bias correction
