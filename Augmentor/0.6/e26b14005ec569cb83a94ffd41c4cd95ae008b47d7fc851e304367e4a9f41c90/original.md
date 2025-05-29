```
ColorJitter <: ColorOperation
```

## Description

Adjusts the brightness and contrast of an image according to the formula `α * image[i] + β * M`, where `M` is either `mean(image)` or the maximum intensity value.

## Usage

```
ColorJitter()
ColorJitter(α, β; [usemax])
```

## Arguments

  * **`α`** : `Real` or `AbstractVector` of `Real` that denote the coefficient(s)   for contrast adjustment. Defaults to `0.8:0.1:1.2`.
  * **`β`** : `Real` or `AbstractVector` of `Real` that denote the coefficient(s)   for brightness adjustment. Defaults to `-0.2:0.1:0.2`.
  * **`usemax::Bool`**: Optional. If `true`, the brightness will be adjusted by   the maximum intensity value; otherwise, the image mean will be used.   Defaults to `true`.

## Examples

```
using Augmentor
img = testpattern()

# use exactly 1.2 for contrast, and one of 0.5 and 0.8 for brightness
augment(img, ColorJitter(1.2, [0.5, 0.8]))

# pick the coefficients randomly from the specified ranges
augment(img, ColorJitter(0.8:0.1:2.0, 0.5:0.1:1.1))
```
