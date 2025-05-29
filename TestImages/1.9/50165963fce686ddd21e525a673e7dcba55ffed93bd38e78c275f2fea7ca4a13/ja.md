```
img = testimage(filename; download_only=false, [ops...])
```

`filename` に部分的に一致するテスト画像をロードします。複数の一致がある場合は、最初の一致が使用されます。

`download_only=true` の場合、フルファイルパスが返されます。その他のキーワード引数 `ops` は、`FileIO.load` を通じて画像 IO バックエンドに渡されます。

# 例

```julia
julia> using TestImages
julia> img = testimage("cameraman.tif"); # フルネーム
julia> img = testimage("cameraman"); # 拡張子なしでも動作
julia> img = testimage("c"); # 部分的な名前でも動作
```

# 拡張ヘルプ

以下はテスト画像の完全なリストです。https://testimages.juliaimages.org/ でも確認できます。

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

```
