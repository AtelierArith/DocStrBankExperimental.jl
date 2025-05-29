Hysteresis thresholding of an image.

```
Usage: bw = hysthresh(img, T1, T2)

Arguments:
           img  - Image to be thresholded
        T1, T2  - Upper and lower threshold values.  T1 and T2
                  can be entered in any order, the larger of the
                  two values is used as the upper threshold.
Returns:
            bw  - The binary thresholded image as a BitArray
```

All pixels with values above threshold T1 are marked as edges. All pixels that are connected to points that have been marked as edges and with values above threshold T2 are also marked as edges. Eight connectivity is used.
