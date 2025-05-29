```
OrganicMaterialsDB(; split=:train, dir=nothing)
```

The OMDB-GAP1 v1.1 dataset from the Organic Materials Database (OMDB) of bulk organic crystals.

The dataset has to be manually downloaded from https://omdb.mathub.io/dataset,  then unzipped and  its file content placed in the `OrganicMaterialsDB` folder.

The dataset contains the following files:

|       Filename |                                                                                              Description |
| --------------:| --------------------------------------------------------------------------------------------------------:|
| structures.xyz |   12500 crystal structures. Use the first 10000 as training examples and the remaining 2500 as test set. |
|   bandgaps.csv |                                                      12500 DFT band gaps corresponding to structures.xyz |
|     CODids.csv | 12500 COD ids cross referencing the Crystallographic Open Database (in the same order as structures.xyz) |

Please cite the paper introducing this dataset: https://arxiv.org/abs/1810.12814
