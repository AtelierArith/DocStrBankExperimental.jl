```
img = testimage(filename; download_only=false, [ops...])
```

Load test image that partially matches `filename`, the first match is used if there're more than one.

If `download_only=true`, the full filepath is returned. Any other keyword arguments `ops` will be passed to image IO backend through `FileIO.load`.

# Example

```julia
julia> using TestImages
julia> img = testimage("cameraman.tif"); # fullname
julia> img = testimage("cameraman"); # without extension works
julia> img = testimage("c"); # with only partial name also works
```

# Extended help

The following is a complete list of testimages, you can also check them at https://testimages.juliaimages.org/

  * `"airplaneF16"`
  * `"autumn_leaves"`
  * `"barbara_color"`
  * `"barbara_gray_512"`
  * `"bark_512"`
  * `"bark_he_512"`
  * `"beach_sand_512"`
  * `"beach_sand_he_512"`
  * `"blobs"`
  * `"brick_wall_512"`
  * `"brick_wall_he_512"`
  * `"calf_leather_512"`
  * `"calf_leather_he_512"`
  * `"cameraman"`
  * `"chelsea"`
  * `"coffee"`
  * `"earth_apollo17"`
  * `"fabio_color_256"`
  * `"fabio_color_512"`
  * `"fabio_gray_256"`
  * `"fabio_gray_512"`
  * `"grass_512"`
  * `"grass_he_512"`
  * `"hela-cells"`
  * `"herringbone_weave_512"`
  * `"herringbone_weave_he_512"`
  * `"house"`
  * `"jetplane"`
  * `"lake_color"`
  * `"lake_gray"`
  * `"lena_color_256"`
  * `"lena_color_512"`
  * `"lena_gray_16bit"`
  * `"lena_gray_256"`
  * `"lena_gray_512"`
  * `"lighthouse"`
  * `"lilly"`
  * `"livingroom"`
  * `"m51"`
  * `"mandril_color"`
  * `"mandril_gray"`
  * `"mandrill"`
  * `"monarch_color"`
  * `"monarch_color_256"`
  * `"moonsurface"`
  * `"morphology_test_512"`
  * `"mountainstream"`
  * `"mri-stack"`
  * `"multi-channel-time-series.ome"`
  * `"peppers_color"`
  * `"peppers_gray"`
  * `"pigskin_512"`
  * `"pigskin_he_512"`
  * `"pirate"`
  * `"plastic_bubbles_512"`
  * `"plastic_bubbles_he_512"`
  * `"raffia_512"`
  * `"raffia_he_512"`
  * `"resolution_test_1920"`
  * `"resolution_test_512"`
  * `"simple_3d_ball"`
  * `"simple_3d_psf"`
  * `"straw_512"`
  * `"straw_he_512"`
  * `"sudoku"`
  * `"toucan"`
  * `"walkbridge"`
  * `"water_512"`
  * `"water_he_512"`
  * `"woman_blonde"`
  * `"woman_darkhair"`
  * `"wood_grain_512"`
  * `"wood_grain_he_512"`
  * `"woolen_cloth_512"`
  * `"woolen_cloth_he_512"`
