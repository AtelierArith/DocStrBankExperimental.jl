```
mvnormlogpdf(μ::A, LorU::A, x::A; ϵ = 1f-8) where A <: AbstractArray
```

Batch version that takes 3D tensors as input where each slice along the 3rd dimension is a batch sample.  `μ` is a (action*size x 1 x batchsize) matrix, `L` is a (action*size x action*size x batchsize), x is a (action*size x action*samples x batchsize).  Return a 3D matrix of size (1 x action*samples x batchsize). 
