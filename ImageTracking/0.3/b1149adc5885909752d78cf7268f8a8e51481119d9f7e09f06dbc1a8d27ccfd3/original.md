```
A, B, C = polynomial_expansion(implementation, img, neighbourhood, σ)
```

Returns the polynomial coefficients of the approximation of the neighbourhood of a point in a 2D function with a polynomial. The expansion is: f(x) = x'Ax + B'x + C

# Options

Various options for the fields of this type are described in more detail below.

## Choices for `implementation`

Selects implementation (`::MatrixImplementation` vs `::ConvolutionImplementation`). The matrix implementation serves as a useful reference against which other faster implementations can be validated.

## Choices for `img`

Grayscale (Float) image whose polynomial expansion is to be found.

## Choices for `window_size`

Determines the size of the pixel neighbourhood used to find polynomial expansion for each pixel; larger values mean that the image will be approximated with smoother surfaces, yielding more robust algorithm and more blurred motion field. The total size equals `2*window_size + 1`.

## Choices for `σ`

Standard deviation of the Gaussian that is used to smooth the image for the purpose of approximating it with a polynomial expansion.

## References

Farnebäck, G.: Polynomial Expansion for Orientation and Motion Estimation. PhD thesis, Linköping University, Sweden, SE-581 83 Linköping, Sweden (2002) Dissertation No 790, ISBN 91-7373-475-6.
