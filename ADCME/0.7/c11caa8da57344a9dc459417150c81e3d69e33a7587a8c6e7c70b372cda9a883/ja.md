```
LinearFlow(indim::Int64, outdim::Int64, A::Union{PyObject, Array{<:Real,2}, Missing}=missing, 
    b::Union{PyObject, Array{<:Real,1}, Missing}=missing, name::Union{String, Missing}=missing)
LinearFlow(A::Union{PyObject, Array{<:Real,2}},
    b::Union{PyObject, Array{<:Real,1}, Missing} = missing; name::Union{String, Missing}=missing)
```

線形フロー演算子を作成します。

$$
x = Az + b
$$

この演算子は必ずしも可逆ではありません。$A$はサイズ`outdim×indim`、$b$は長さ`outdim`のベクトルです。

# 例 1: 可逆なAを使用してガウス乱数変数を再構成する

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
run(sess, flows[1].b) # おおよそ [2.0 3.0]
run(sess, flows[1].A * flows[1].A') # おおよそ [2.0 1.0;1.0 2.0]
```

# 例 2: 非可逆なAを使用してガウス乱数変数を再構成する

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
run(sess, b[1]*2 + b[2]) # おおよそ 6.0
```
