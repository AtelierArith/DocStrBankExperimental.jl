```
motionlist = MotionList(motions...)
```

MotionList struct. The other option, instead of `NoMotion`,  is to define a dynamic phantom by means of the `MotionList` struct. It is composed by one or more [`Motion`](@ref) instances. 

# Arguments

  * `motions`: (`::Vector{Motion{T<:Real}}`) vector of `Motion` instances

# Returns

  * `motionlist`: (`::MotionList`) MotionList struct

# Examples

```julia-repl
julia>  motionlist = MotionList(
            Motion(
                action = Translate(0.01, 0.0, 0.02),
                time = TimeRange(0.0, 1.0),
                spins = AllSpins()
            ),
            Motion(
                action = Rotate(0.0, 0.0, 45.0),
                time = Periodic(1.0),
                spins = SpinRange(1:10)
            )
        )
```
