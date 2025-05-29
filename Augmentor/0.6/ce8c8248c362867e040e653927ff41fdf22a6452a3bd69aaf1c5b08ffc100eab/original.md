```
GaussianBlur <: ColorOperation
```

## Description

Blurs an image using a Gaussian filter.

## Usage

```
GaussianBlur(k, [σ])
```

## Arguments

  * **`k`** : `Integer` or `AbstractVector` of `Integer` that denote   the kernel size. It must be an odd positive number.
  * **`σ`** : Optional. `Real` or `AbstractVector` of `Real` that denote the   standard deviation. It must be a positive number.   Defaults to `0.3 * ((k - 1) / 2 - 1) + 0.8`.

## Examples

```
using Augmentor
img = testpattern()

# use exactly k=3 and σ=1.0
augment(img, GaussianBlur(3, 1.0))

# pick k and σ randomly from the specified ranges
augment(img, GaussianBlur(3:2:7, 1.0:0.1:2.0))
```
