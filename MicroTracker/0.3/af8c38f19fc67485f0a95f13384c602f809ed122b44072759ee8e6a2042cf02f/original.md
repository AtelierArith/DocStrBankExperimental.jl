```
loadframe(vidname::AbstractString, framenumber::Integer)
```

Return an image corresponding to the `framenumber` frame in the video `vidname`. Must be present in the `original_video` folder.

It looks at the way the tifs are automatically named and matches the pattern. **Does not necessarily** match the real frame number in the data, especially if there is no particle in the first frame.

Normally, images from ImageJ index at 0, while Julia indexes at one. Therefore, this function will return the image named with `framenumber-1`.
