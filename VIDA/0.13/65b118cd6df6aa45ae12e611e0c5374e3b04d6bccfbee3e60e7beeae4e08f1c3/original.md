```julia
clipimage(clip, image)
clipimage(clip, image, mode)

```

Clips the image `im` according to the value clip. There are two modes for image clipping:     - `:relative` which zeros the pixels whose intensity are below `clip` relative to the max.     - `:absolute` which zeros the pixels whose intensity is below `clip` in Jy/pixel
