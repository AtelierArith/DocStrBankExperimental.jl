```
serializable(mach::Machine)
```

Returns a shallow copy of the machine to make it serializable. In particular, all training data is removed and, if necessary, learned parameters are replaced with persistent representations.

Any general purpose Julia serializer may be applied to the output of `serializable` (eg, JLSO, BSON, JLD) but you must call `restore!(mach)` on the deserialised object `mach` before using it. See the example below.

If using Julia's standard Serialization library, a shorter workflow is available using the [`MLJBase.save`](@ref) (or `MLJ.save`) method.

A machine returned by `serializable` is characterized by the property `mach.state == -1`.

### Example using [JLSO](https://invenia.github.io/JLSO.jl/stable/)

```julia
using MLJ
using JLSO
Tree = @load DecisionTreeClassifier
tree = Tree()
X, y = @load_iris
mach = fit!(machine(tree, X, y))

# This machine can now be serialized
smach = serializable(mach)
JLSO.save("machine.jlso", :machine => smach)

# Deserialize and restore learned parameters to useable form:
loaded_mach = JLSO.load("machine.jlso")[:machine]
restore!(loaded_mach)

predict(loaded_mach, X)
predict(mach, X)
```

See also [`restore!`](@ref), [`MLJBase.save`](@ref).
