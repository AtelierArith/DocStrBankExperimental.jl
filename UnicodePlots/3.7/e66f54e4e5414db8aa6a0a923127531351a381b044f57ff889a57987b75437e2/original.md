```
contourplot(A; kw...)
```

# Usage

Draws a contour plot of matrix `A` along axis `x` and `y` on a new canvas.

The `y` axis is flipped by default:

```
Julia matrices (images) │ UnicodePlots
                        │
           axes(A, 2)   │
           o───────→    │   ↑
           │            │   │
axes(A, 1) │            │ y │
           │            │   │
           ↓            │   o───────→
                        │       x
```
