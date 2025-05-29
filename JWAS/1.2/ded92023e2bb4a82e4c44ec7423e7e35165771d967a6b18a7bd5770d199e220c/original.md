```
GWAS(model,map_file,marker_effects_file...;
     window_size = "1 Mb",sliding_window = false,
     GWAS = true, threshold = 0.001,
     genetic_correlation = false,
     header = true)
```

run genomic window-based GWAS

  * MCMC samples of marker effects are stored in **marker*effects*file** with delimiter ','.
  * **model** is either the model::MME used in analysis or the genotype cavariate matrix M::Array
  * **map_file** has the (sorted) marker position information with delimiter ','. If the map file is not provided, i.e., **map_file**=`false`, a fake map file will be generated with **window_size** markers in each 1 Mb window, and each 1 Mb window will be tested.
  * If two **marker*effects*file** are provided, and **genetic_correlation** = true, genomic correlation for each window is calculated.
  * Statistics are computed for nonoverlapping windows of size *window_size* by default. If **sliding_window** = true, those for overlapping sliding windows are calculated.
  * map file format:

```
markerID,chromosome,position
m1,1,16977
m2,1,434311
m3,1,1025513
m4,2,70350
m5,2,101135
```
