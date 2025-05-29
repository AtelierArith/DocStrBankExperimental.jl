```
GroupNorm(chs::Integer, groups::Integer, activation=identity; init_bias=zeros32,
          init_scale=ones32, affine=true, epsilon=1f-5)
```

[Group Normalization](https://arxiv.org/abs/1803.08494) layer.

## Arguments

  * `chs`: Size of the channel dimension in your data. Given an array with `N` dimensions, call the `N-1`th the channel dimension. For a batch of feature vectors this is just the data dimension, for `WHCN` images it's the usual channel dimension.
  * `groups` is the number of groups along which the statistics are computed. The number of channels must be an integer multiple of the number of groups.
  * `activation`: After normalization, elementwise activation `activation` is applied.

## Keyword Arguments

  * `epsilon`: a value added to the denominator for numerical stability
  * If `affine=true`, it also applies  a shift and a rescale to the input through to learnable per-channel bias and scale parameters.

      * `init_bias`: Controls how the `bias` is initialized
      * `init_scale`: Controls how the `scale` is initialized

# Extended Help

## Inputs

  * `x`: Array where `size(x, N - 1) = chs` and `ndims(x) > 2`

## Returns

  * `y`: Normalized Array
  * Update model state

## Parameters

  * `affine=true`

      * `bias`: Bias of shape `(chs,)`
      * `scale`: Scale of shape `(chs,)`
  * `affine=false` - Empty `NamedTuple()`

## States

  * `training`: Used to check if training/inference mode

Use `Lux.testmode` during inference.

## Example

```jldoctest
julia> Chain(Dense(784 => 64), GroupNorm(64, 4, relu), Dense(64 => 10), GroupNorm(10, 5))
Chain(
    layer_1 = Dense(784 => 64),         # 50_240 parameters
    layer_2 = GroupNorm(64, 4, relu, affine=true),  # 128 parameters
    layer_3 = Dense(64 => 10),          # 650 parameters
    layer_4 = GroupNorm(10, 5, affine=true),  # 20 parameters
)         # Total: 51_038 parameters,
          #        plus 0 states.
```

See also [`GroupNorm`](@ref), [`InstanceNorm`](@ref), [`LayerNorm`](@ref), [`WeightNorm`](@ref)
