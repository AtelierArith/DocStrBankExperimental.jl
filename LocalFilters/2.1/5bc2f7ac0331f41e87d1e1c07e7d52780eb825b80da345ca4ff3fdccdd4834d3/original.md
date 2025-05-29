```
const LocalFilters.Box{N} = FastUniformArray{Bool,N,true}
```

is an alias to the type of uniformly `true` `N`-dimensional arrays. Instances of this kind are used to represent hyper-rectangular sliding windows in `LocalFilters`.

Method [`LocalFilters.box`](@ref) can be used to build an object of this type.
