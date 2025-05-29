```
Zscale(options)(data)
```

PlotUtils.zscaleをデフォルトパラメータで呼び出せるようにラップします。これは、IRAFに由来する天文学データを積極的に伸ばして微弱な構造を確認するための一般的なアルゴリズムであり、現在では多くの他のアプリケーション/ライブラリ（DS9、Astropyなど）でも見られます。

使用法:

```julia
imview(img, clims=Zscale())
implot(img, clims=Zscale(contrast=0.1))
```

デフォルトパラメータ:

```
nsamples::Int=1000
contrast::Float64=0.25
max_reject::Float64=0.5
min_npixels::Float64=5
k_rej::Float64=2.5
max_iterations::Int=5
```
