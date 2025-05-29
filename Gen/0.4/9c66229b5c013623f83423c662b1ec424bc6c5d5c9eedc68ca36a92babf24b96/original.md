ProductDistribution(distributions::Vararg{<:Distribution})

Define new distribution that is the product of the given nonempty list of distributions having a common type.

The arguments comprise the list of base distributions.

Example:

```julia
normal_strip = ProductDistribution(uniform, normal)
```

The resulting product distribution takes `n` arguments, where `n` is the sum of the numbers of arguments taken by each distribution in the list. These arguments are the arguments to each component distribution, in the order in which the distributions are passed to the constructor.

Example:

```julia
@gen function unit_strip_and_near_seven()
    x ~ flip_and_number(0.0, 0.1, 7.0, 0.01)
end
```
