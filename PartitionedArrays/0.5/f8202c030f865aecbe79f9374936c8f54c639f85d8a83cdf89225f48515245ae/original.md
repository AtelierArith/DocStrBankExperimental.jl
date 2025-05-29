```
struct GenericJaggedArray{V,A,B}
```

Generalization of `JaggedArray`, where the fields `data` and `ptrs` are allowed to be any array-like object.

# Properties

```
data::A
ptrs::B
```

# Supertype hierarchy

```
GenericJaggedArray{V,A,B} <: AbstractVector{V}
```

Given `a::GenericJaggedArray`, `V` is `typeof(view(a.data,a.ptrs[i]:(a.ptrs[i+1]-1)))`.
