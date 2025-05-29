```
richardson_lucy_iterative(measured, psf; <keyword arguments>)
```

古典的な反復リチャードソン-ルーシー反復スキームによるデコンボリューション。`measured`は測定された配列で、`psf`は点拡散関数です。最適化アプローチの`deconvolution`よりも収束が遅いです。

# キーワード引数

  * `regularizer=GR()`: 正則化関数。交換可能です。
  * `λ=0.05`: 正則化器の全体的な損失関数に対する重み付けを示す浮動小数点数。
  * `iterations=100`: 反復回数を指定します。
  * `progress`: `nothing`でない場合、進行状況はDeconvOptim.options*trace*deconv()によって得られる要約辞書で監視されます。

# 例

```julia-repl
julia> using DeconvOptim, TestImages, Colors, Noise;

julia> img = Float32.(testimage("resolution_test_512"));

julia> psf = Float32.(generate_psf(size(img), 30));

julia> img_b = conv(img, psf);

julia> img_n = poisson(img_b, 300);

julia> @time res = richardson_lucy_iterative(img_n, psf);
```
