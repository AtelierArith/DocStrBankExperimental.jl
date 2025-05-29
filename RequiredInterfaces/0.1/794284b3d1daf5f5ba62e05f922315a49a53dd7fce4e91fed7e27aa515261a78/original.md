```
@required MyInterface func(::Foo, ::MyInterface)
@required MyInterface function func(::Foo, ::MyInterface) end
@required MyInterface begin
    foo(::B, ::MyInterface)
    bar(::A, ::MyInterface)
end
```

Marks all occurences of `MyInterface` in the given function signatures as part of the interface `MyInterface`. Also defines fallback methods, which throw a [`NotImplementedError`](@ref) when called with an argument that doesn't implement this mandatory function.

Throws an `ArgumentError` if `MyInterface` is not an abstract type or the given expression doesn't conform to the three shown styles. The function body of the second style is expected to be empty - `@required` can't be used to mark fallback implementations as part of a user-implementable interface. Its sole purpose is marking parts of an API that a user needs to implement to be able to have functions expecting that interface work.
