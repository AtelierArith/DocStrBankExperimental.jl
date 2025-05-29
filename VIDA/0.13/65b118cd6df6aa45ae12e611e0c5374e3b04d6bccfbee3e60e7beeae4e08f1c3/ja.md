```julia
clipimage(clip, image)
clipimage(clip, image, mode)

```

画像 `im` をクリップ値に従ってクリップします。画像クリッピングには2つのモードがあります:     - `:relative` は、最大値に対して `clip` よりも強度が低いピクセルをゼロにします。     - `:absolute` は、Jy/ピクセルで `clip` よりも強度が低いピクセルをゼロにします。
