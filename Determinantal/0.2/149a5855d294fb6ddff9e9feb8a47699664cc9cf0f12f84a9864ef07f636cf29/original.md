ProjectionEnsemble(V::Matrix{T},orth=true)

Construct a projection ensemble from a matrix of features. Here we assume $\mathbf{L} = \mathbf{V}\mathbf{V}^t$, so that V must be n \times r, where n is the number of items and r is the rank. V needs not be orthogonal. If orth is set to true (default), then a QR decomposition is performed. If V is orthogonal already, then this computation may be skipped, and you can set orth to false.
