```
Either <: Augmentor.ImageOperation
```

## Description

Chooses between the given `operations` at random when applied. This is particularly useful if one for example wants to first either rotate the image 90 degree clockwise or anticlockwise (but never both), and then apply some other operation(s) afterwards.

When compiling a pipeline, `Either` will analyze the provided `operations` in order to identify the preferred formalism to use when applied. The chosen formalism is chosen such that it is supported by all given `operations`. This way the output of applying `Either` will be inferable and the whole pipeline will remain type-stable (even though randomness is involved).

By default each specified image operation has the same probability of occurrence. This default behaviour can be overwritten by specifying the `chance` manually.

## Usage

```
Either(operations, [chances])

Either(operations...; [chances])

Either(pairs...)

*(operations...)

*(pairs...)
```

## Arguments

  * **`operations`** : `NTuple` or `Vararg` of `Augmentor.ImageOperation`   that denote the possible choices to sample from when applied.
  * **`chances`** : Optional. Denotes the relative chances for an   operation to be sampled. Has to contain the same number of   elements as `operations`. Either an `NTuple` of numbers if   specified as positional argument, or alternatively a   `AbstractVector` of numbers if specified as a keyword   argument. If omitted every operation will have equal   probability of occurring.
  * **`pairs`** : `Vararg` of `Pair{<:Real,<:Augmentor.ImageOperation}`.   A compact way to specify an operation and its chance of   occurring together.

## See also

[`NoOp`](@ref), [`augment`](@ref)

## Examples

```julia
using Augmentor
img = testpattern()

# all three operations have equal chance of occuring
augment(img, Either(FlipX(), FlipY(), NoOp()))
augment(img, FlipX() * FlipY() * NoOp())

# NoOp is twice as likely as either FlipX or FlipY
augment(img, Either(1=>FlipX(), 1=>FlipY(), 2=>NoOp()))
augment(img, Either(FlipX(), FlipY(), NoOp(), chances=[1,1,2]))
augment(img, Either((FlipX(), FlipY(), NoOp()), (1,1,2)))
augment(img, (1=>FlipX()) * (1=>FlipY()) * (2=>NoOp()))
```
