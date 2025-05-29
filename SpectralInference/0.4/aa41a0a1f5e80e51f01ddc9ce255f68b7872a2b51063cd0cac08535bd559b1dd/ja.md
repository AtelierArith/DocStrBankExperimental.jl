```
vmeasure_homogeneity_completeness(labels_true, labels_pred; β=1.)
```

はv-measure、均質性、完全性を計算して返します。これはそれぞれfスコア、精度、再現率に似ています。

引数:

  * β、v-measureの重み付け項。βが1より大きい場合、完全性が計算でより強く重視され、βが1より小さい場合、均質性がより強く重視されます。

引用:

  * A. Rosenberg, J. Hirschberg, in Proceedings of the 2007 Joint Conference

on Empirical Methods in Natural Language Processing and Computational Natural  Language Learning (EMNLP-CoNLL) (Association for Computational Linguistics,   Prague, Czech Republic, 2007; https://aclanthology.org/D07-1043), pp. 410–420.
