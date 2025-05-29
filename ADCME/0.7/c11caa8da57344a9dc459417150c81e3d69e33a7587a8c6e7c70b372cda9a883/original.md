```
LinearFlow(indim::Int64, outdim::Int64, A::Union{PyObject, Array{<:Real,2}, Missing}=missing, 
    b::Union{PyObject, Array{<:Real,1}, Missing}=missing, name::Union{String, Missing}=missing)
LinearFlow(A::Union{PyObject, Array{<:Real,2}},
    b::Union{PyObject, Array{<:Real,1}, Missing} = missing; name::Union{String, Missing}=missing)
```

Creates a linear flow operator, 

$$
x = Az + b
$$

The operator is not necessarily invertible. $A$ has the size `outdim×indim`, $b$ is a length `outdim` vector.

# Example 1: Reconstructing a Gaussian random variable using invertible A

```julia
using ADCME
using Distributions 

d = MvNormal([2.0;3.0],[2.0 1.0;1.0 2.0])
flows = [LinearFlow(2, 2)]
prior = ADCME.MultivariateNormalDiag(loc = zeros(2))
model = NormalizingFlowModel(prior, flows)
x = rand(d, 10000)'|>Array
zs, prior_logpdf, logdet = model(x)
log_pdf = prior_logpdf + logdet
loss = -sum(log_pdf)
sess = Session(); init(sess)
BFGS!(sess, loss)
run(sess, flows[1].b) # approximately [2.0 3.0]
run(sess, flows[1].A * flows[1].A') # approximate [2.0 1.0;1.0 2.0]
```

# Example 2: Reconstructing a Gaussian random variable using non-invertible A

```julia
using ADCME
using Distributions 

d = Normal()
A = reshape([2. 1.], 2, 1)
b = Variable(ones(2)) 
flows = [LinearFlow(A, b)]
prior = ADCME.MultivariateNormalDiag(loc = zeros(1))
model = NormalizingFlowModel(prior, flows)

x = rand(d, 10000, 1)
x = x * [2.0 1.0] .+ [1.0 3.0]

x = [2.0 2.0]
zs, prior_logpdf, logdet = model(x)
log_pdf = prior_logpdf + logdet
loss = -sum(log_pdf)
sess = Session(); init(sess)
BFGS!(sess, loss)
run(sess, b[1]*2 + b[2]) # approximate 6.0
```
