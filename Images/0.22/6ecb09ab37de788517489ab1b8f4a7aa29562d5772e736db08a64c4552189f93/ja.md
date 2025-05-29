コンストラクタ、変換、および特性:

```
- コンストラクション: 専門パッケージのコンストラクタを使用します。例: `AxisArray`, `ImageMeta` など。
- "変換": `colorview`, `channelview`, `rawview`, `normedview`, `permuteddimsview`
- 特性: `pixelspacing`, `sdims`, `timeaxis`, `timedim`, `spacedirections`
```

コントラスト/色彩:

```
- `clamp01`, `clamp01nan`, `scaleminmax`, `colorsigned`, `scalesigned`
```

アルゴリズム:

```
- 削減: `maxfinite`, `maxabsfinite`, `minfinite`, `meanfinite`, `integral_image`, `boxdiff`, `gaussian_pyramid`
- リサイズ: `restrict`, `imresize` (まだエクスポートされていません)
- フィルタリング: `imfilter`, `imfilter!`, `mapwindow`, `imROF`, `padarray`
- フィルタリングカーネル: `Kernel.` または `KernelFactors.`, の後に `ando[345]`, `guassian2d`, `imaverage`, `imdog`, `imlaplacian`, `prewitt`, `sobel`
- 露出: `imhist`, `histeq`, `adjust_gamma`, `histmatch`, `imadjustintensity`, `imstretch`, `imcomplement`, `clahe`, `cliphist`
- 勾配: `backdiffx`, `backdiffy`, `forwarddiffx`, `forwarddiffy`, `imgradients`
- エッジ検出: `imedge`, `imgradients`, `thin_edges`, `magnitude`, `phase`, `magnitudephase`, `orientation`, `canny`
- コーナー検出: `imcorner`, `imcorner_subpixel`, `harris`, `shi_tomasi`, `kitchen_rosenfeld`, `meancovs`, `gammacovs`, `fastcorners`
- ブロブ検出: `blob_LoG`, `findlocalmaxima`, `findlocalminima`
- 形態学的操作: `dilate`, `erode`, `closing`, `opening`, `tophat`, `bothat`, `morphogradient`, `morpholaplace`, `feature_transform`, `distance_transform`, `convexhull`
- 接続成分: `label_components`, `component_boxes`, `component_lengths`, `component_indices`, `component_subscripts`, `component_centroids`
- 補間: `bilinear_interpolation`
```

テスト画像とファントム (TestImages.jlも参照):

```
- `shepp_logan`
```
