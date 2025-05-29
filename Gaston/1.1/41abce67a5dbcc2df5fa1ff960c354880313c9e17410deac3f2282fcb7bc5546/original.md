```
imagesc([x,] [y,] z, [axes,] args...) -> Gaston.Figure
```

Plot an image given by array `z`. If the array is a matrix, a grayscale image is assumed. If the array is three-dimensional, an rgbimage is assumed, with `z[1,:,:]` the red channel, `z[2,:,:]` the blue channel, and `z[3,:,:]` the blue channel.
