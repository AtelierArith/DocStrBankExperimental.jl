```
CCIPCA(outdim::Int, indim; l::Int)
```

Online PCA with the CCIPCA (Candid Covariance-free Incremental PCA) algorithm, where indim is the length of incoming vectors, outdim is the number of dimension to project to, and l is the level of amnesia. Give values of l in the range 2-4 if you want old vectors to be gradually less important, i.e. latest vectors added get more weight.

If no indim is specified it will be set later, on first call to fit. After that it is fixed and cannot change.

The CCIPCA is a very fast, simple, and online approximation of PCA. It can be used for Dimensionality Reduction to project high-dimensional vectors into a low-dimensional (typically 2D or 3D) space. This algorithm has shown very good properties in comparative studies; it is both fast and give a good approximation to (batch) PCA.

# Example

```
o = CCIPCA(2, 10)                # Project 10-dimensional vectors into 2D
u1 = rand(10)
fit!(o, u1)                      # Fit to u1
u2 = rand(10)
fit!(o, u2)                      # Fit to u2
u3 = rand(10)
OnlineStats.transform(o, u3)     # Project u3 into PCA space fitted to u1 and u2 but don't change the projection
u4 = rand(10)
OnlineStats.fittransform!(o, u4) # Fit u4 and then project u4 into the space
sort!(o)                         # Sort from high to low eigenvalues
o[1]                             # Get primary (1st) eigenvector
OnlineStats.relativevariances(o)         # Get the variation (explained) "by" each eigenvector
```
