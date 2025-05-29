Some runtime parameters. The default value is after the `=`

## step 1:

```julia
bm3d_config.thr_patchSize = CartesianIndex(8, 8)	size of patches;
bm3d_config.thr_searchStride = CartesianIndex(3, 3)	In order to speed up the processing,the loop over the pixels of the imageis done with a stepp(integer) in row and column;
bm3d_config.thr_searchWin = CartesianIndex(19, 19)	search window size;
bm3d_config.thr_nMatch = 31	maximum number of similar patches kept;
bm3d_config.thr_thresh3D = 2.7	3D group hreshold;
bm3d_config.thr_distFunction = Euclidean2	A function that measures the distance between blocks;
bm3d_config.thr_group_transform! = FFTW.dct!	A function that 3D transform in group
bm3d_config.thr_group_itransform! = FFTW.idct!	A function that 3D inverse transform in group;
```

## step2:

```julia
bm3d_config.wie_patchSize = CartesianIndex(8, 8)	size of patches;
bm3d_config.wie_searchStride = CartesianIndex(3, 3)	In order to speed up the processing,the loop over the pixels of the imageis done with a stepp(integer) in row and column;
bm3d_config.wie_searchWin = CartesianIndex(11, 11)	search window size;
bm3d_config.wie_nMatch = 15	maximum number of similar patches kept;
bm3d_config.wie_distFunction = Euclidean2	A function that measures the distance between blocks;
bm3d_config.wie_group_transform! = FFTW.dct!	A function that 3D transform in group;
bm3d_config.wie_group_itransform! = FFTW.idct!	A function that 3D inverse transform in group;
```

## others

bm3d*config.show*info = false	show some running message

note:

The 3D group data struct:

```
G3D[k, :, :]	# k-th matching block.
size(G3D)	# (nMatch, patchSize[1], patchSize[2])
```
