Constructors, conversions, and traits:

```
- Construction: use constructors of specialized packages, e.g., `AxisArray`, `ImageMeta`, etc.
- "Conversion": `colorview`, `channelview`, `rawview`, `normedview`, `permuteddimsview`
- Traits: `pixelspacing`, `sdims`, `timeaxis`, `timedim`, `spacedirections`
```

Contrast/coloration:

```
- `clamp01`, `clamp01nan`, `scaleminmax`, `colorsigned`, `scalesigned`
```

Algorithms:

```
- Reductions: `maxfinite`, `maxabsfinite`, `minfinite`, `meanfinite`, `integral_image`, `boxdiff`, `gaussian_pyramid`
- Resizing: `restrict`, `imresize` (not yet exported)
- Filtering: `imfilter`, `imfilter!`, `mapwindow`, `imROF`, `padarray`
- Filtering kernels: `Kernel.` or `KernelFactors.`, followed by `ando[345]`, `guassian2d`, `imaverage`, `imdog`, `imlaplacian`, `prewitt`, `sobel`
- Exposure : `imhist`, `histeq`, `adjust_gamma`, `histmatch`, `imadjustintensity`, `imstretch`, `imcomplement`, `clahe`, `cliphist`
- Gradients: `backdiffx`, `backdiffy`, `forwarddiffx`, `forwarddiffy`, `imgradients`
- Edge detection: `imedge`, `imgradients`, `thin_edges`, `magnitude`, `phase`, `magnitudephase`, `orientation`, `canny`
- Corner detection: `imcorner`,`imcorner_subpixel`, `harris`, `shi_tomasi`, `kitchen_rosenfeld`, `meancovs`, `gammacovs`, `fastcorners`
- Blob detection: `blob_LoG`, `findlocalmaxima`, `findlocalminima`
- Morphological operations: `dilate`, `erode`, `closing`, `opening`, `tophat`, `bothat`, `morphogradient`, `morpholaplace`, `feature_transform`, `distance_transform`, `convexhull`
- Connected components: `label_components`, `component_boxes`, `component_lengths`, `component_indices`, `component_subscripts`, `component_centroids`
- Interpolation: `bilinear_interpolation`
```

Test images and phantoms (see also TestImages.jl):

```
- `shepp_logan`
```
