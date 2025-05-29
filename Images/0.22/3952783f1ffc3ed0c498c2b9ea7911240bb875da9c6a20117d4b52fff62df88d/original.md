```
corners = imcorner(img; [method])
corners = imcorner(img, threshold; [method])
```

Performs corner detection using one of the following methods -

```
1. harris
2. shi_tomasi
3. kitchen_rosenfeld
```

The parameters of the individual methods are described in their documentation. The maxima values of the resultant responses are taken as corners. If a threshold is specified, the values of the responses are thresholded to give the corner pixels. If `threshold` is a `Percentile` then its type will be preserved.
