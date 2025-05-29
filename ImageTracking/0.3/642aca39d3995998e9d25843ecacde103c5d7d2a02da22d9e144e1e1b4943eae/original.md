```
Farneback(Args...)
```

A method for dense optical flow estimation developed by Gunnar Farneback. It computes the optical flow for all the points in the frame using the polynomial representation of the images. The idea of polynomial expansion is to approximate the neighbourhood of a point in a 2D function with a polynomial. Displacement fields are estimated from the polynomial coefficients depending on how the polynomial transforms under translation.

# Options

Various options for the fields of this type are described in more detail below.

## Choices for `iterations`

Number of iterations the displacement estimation algorithm is run at each point. If left unspecified a default value of seven iterations is assumed.

## Choices for `estimation_window`

Determines the neighbourhood size over which information will be intergrated when determining the displacement of a pixel. The total size equals `2*estimation_window + 1`. If left unspecified a default value of eleven is assumed.

## Choices for `σ_estimation_window`

Standard deviation of a Gaussian weighting filter used to weigh the contribution of a pixel's neighbourhood when determining the displacement of a pixel. If left unspecified a default value of nine is assumed.

## Choices for `expansion_window`

Determines the size of the pixel neighbourhood used to find polynomial expansion for each pixel; larger values mean that the image will be approximated with smoother surfaces, yielding more robust algorithm and more blurred motion field. The total size equals `2*expansion_window + 1`. If left unspecified a default value of six is assumed.

## Choices for `σ_expansion_window`

Standard deviation of the Gaussian that is used to smooth the image for the purpose of approximating it with a polynomial expansion. If left unspecified a default value of five is assumed.

# References

1. Farnebäck G. (2003) Two-Frame Motion Estimation Based on Polynomial Expansion. In: Bigun J., Gustavsson T. (eds) Image Analysis. SCIA 2003. Lecture Notes in Computer Science, vol 2749. Springer, Berlin, Heidelberg
2. Farnebäck, G.: Polynomial Expansion for Orientation and Motion Estimation. PhD thesis, Linköping University, Sweden, SE-581 83 Linköping, Sweden (2002) Dissertation No 790, ISBN 91-7373-475-6.
