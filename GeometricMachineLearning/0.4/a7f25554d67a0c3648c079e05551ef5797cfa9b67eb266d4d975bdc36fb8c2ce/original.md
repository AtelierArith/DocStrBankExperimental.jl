```
optimize_for_one_epoch!(opt, model, ps, dl, batch, loss, λY)
```

Sample the data contained in `dl` according to `batch` and optimize for these batches.

This step also performs automatic differentiation on `loss`.

The output of `optimize_for_one_epoch!` is the average loss over all batches of the epoch:

$$
output = \frac{1}{\mathtt{steps\_per\_epoch}}\sum_{t=1}^\mathtt{steps\_per\_epoch}\mathtt{loss}(\theta^{(t-1)}).
$$

This is done because any *reverse differentiation* routine always has two outputs; for `Zygote`:

```julia
loss_value, pullback = Zygote.pullback(ps -> loss(model, ps, input, output), ps)
```

So we get the value for the loss for free whenever we compute the pullback with AD.

# Arguments

All the arguments are mandatory (there are no defaults): 

1. an instance of [`Optimizer`](@ref).
2. the neural network model.
3. the neural network parameters `ps`.
4. the data (i.e. an instance of [`DataLoader`](@ref)).
5. `batch`::[`Batch`](@ref): stores `batch_size` (and optionally `seq_length` and `prediction_window`).
6. `loss::NetworkLoss`.
7. the *section* `λY` of the parameters `ps`.

# Implementation

Internally this calls [`optimization_step!`](@ref) for each minibatch.

The number of minibatches can be determined with [`number_of_batches`](@ref):

```jldoctest
using GeometricMachineLearning
using GeometricMachineLearning: number_of_batches

data = [1, 2, 3, 4, 5]
batch = Batch(2)
dl = DataLoader(data; suppress_info = true)

number_of_batches(dl, batch)

# output

3
```
