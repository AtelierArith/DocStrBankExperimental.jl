```
Linear()
```

Quality function that interpolates all scaled data points to a single master curve. For every data point, we take the closest data points, to the left and to the right to interpolate a linear function. The quality is then calculated as the sum of the squared differences between the data points and the interpolated values.
