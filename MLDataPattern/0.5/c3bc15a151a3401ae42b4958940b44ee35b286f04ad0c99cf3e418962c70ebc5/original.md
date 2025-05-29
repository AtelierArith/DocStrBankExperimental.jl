```
slidingwindow(f, data, size, [stride], [excludetarget], [obsdim]) -> LabeledSlidingWindow
```

Return a vector-like view of the `data` for which each element is a tuple of two elements:

1. A fixed size "window" of `size` adjacent observations. By default these windows are not overlapping. This can be changed by explicitly specifying a `stride`.
2. A single target (or vector of targets) for the window. The content of the target(s) is defined by the label-index function `f`.

The label-index function `f` is a unary function that takes the index of the first observation in the current window and should return the index (or indices) of the associated target(s) for that window.

```julia-repl
julia> A = slidingwindow(i->i+6, 1:20, 6)
3-element slidingwindow(::##3#4, ::UnitRange{Int64}, 6) with element type Tuple{...}
 ([1, 2, 3, 4, 5, 6], 7)
 ([7, 8, 9, 10, 11, 12], 13)
 ([13, 14, 15, 16, 17, 18], 19)
```

Note that only complete and in-bound windows are included in the output, which implies that it is possible for excess observations to be omitted from the resulting view.

```julia-repl
julia> A = slidingwindow(i->i-1, 1:20, 6)
2-element slidingwindow(::##5#6, ::UnitRange{Int64}, 6) with element type Tuple{...}
 ([7, 8, 9, 10, 11, 12], 6)
 ([13, 14, 15, 16, 17, 18], 12)
```

As hinted above, it is also allowed for `f` to return a vector of indices. This can be useful for emulating techniques such as skip-gram.

```julia-repl
julia> data = split("The quick brown fox jumps over the lazy dog")
9-element Array{SubString{String},1}:
 "The"
 "quick"
 ⋮
 "lazy"
 "dog"

julia> A = slidingwindow(i->[i-2:i-1; i+1:i+2], data, 1)
5-element slidingwindow(::##11#12, ::Array{SubString{String},1}, 1) with element type Tuple{...}:
 (["brown"], ["The", "quick", "fox", "jumps"])
 (["fox"], ["quick", "brown", "jumps", "over"])
 (["jumps"], ["brown", "fox", "over", "the"])
 (["over"], ["fox", "jumps", "the", "lazy"])
 (["the"], ["jumps", "over", "lazy", "dog"])
```

Should it so happen that the targets overlap with the features, then the affected observation(s) will be present in both. To change this behaviour one can set the optional parameter `excludetarget = true`. This will remove the target(s) from the feature window.

```julia-repl
julia> slidingwindow(i->i+2, data, 5, stride = 1, excludetarget = true)
5-element slidingwindow(::##17#18, ::Array{SubString{String},1}, 5, stride = 1) with element type Tuple{...}:
 (["The", "quick", "fox", "jumps"], "brown")
 (["quick", "brown", "jumps", "over"], "fox")
 (["brown", "fox", "over", "the"], "jumps")
 (["fox", "jumps", "the", "lazy"], "over")
 (["jumps", "over", "lazy", "dog"], "the")
```

The optional (keyword) parameter `obsdim` allows one to specify which dimension denotes the observations. see `LearnBase.ObsDim` for more detail.
