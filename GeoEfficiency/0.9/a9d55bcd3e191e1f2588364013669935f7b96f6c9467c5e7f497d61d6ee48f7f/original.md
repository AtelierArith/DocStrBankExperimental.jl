The function `batch()` can be called with or without arrangement(s).  The without argument version relay on previously prepared Comma Saved   Values [CSV] files, that can be easily edit by Microsoft Excel,  by default located in the directory **`/home/terasaki/GeoEfficiency`** .

results of batch calculation are saved on a **`CSV`**  file(s) named after the detector(s).  the **`CSV`**  file by default found in **`/home/terasaki/GeoEfficiency/results`**.

# CSV input files

  * `Detectors.csv` contains the detectors description; The line format is:

```
	 Crystal_Radius | Crystal_Length | Hole_Radius | Hole_Depth |
	 ---------------| ---------------|-------------|----------- |
```

  * `srcHeights.csv` contains the source heights;

```
	 Source_Heights | 
	 ---------------|
```

  * `srcRhos.csv` contains the source off-axis distances;

```
	 Source_Rhos | 
 	 ------------|
```

  * `srcRadii.csv` contains the source radii for disc and cylindrical sources;

```
	 Source_Radii| 
	 ------------|
```

  * `srcLengths.csv` contains the source length for cylindrical sources;

```
	 Source_Lengths| 
	 --------------|
```

# CSV results files

**`CSV`**  file containing the results has columns of headers   `AnchorHeight`, `AnchorRho`, `srcRadius`, `srcLength`, `GeoEfficiency` for `non-point` sources   and columns of headers `Height`, `Rho`, `GeoEfficiency` for `point` sources.

!!! note
    for Comma Saved Values [CSV] files each line represent an entry,   the first line is always treated as the header.


!!! warning
    the program expect each line to contain one number for all CSV files except  for `Detectors.csv` each line should contain at least one number or at   most four separated numbers.

