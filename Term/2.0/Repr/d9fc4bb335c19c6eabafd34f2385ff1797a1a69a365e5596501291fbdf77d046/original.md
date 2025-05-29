with_repr(typedef::Expr)

Function for the macro @with_repr which creates a `Base.show` method for a type.

The `show` method shows the field names/types for the  type and the values of the fields.

# Example

```
@with_repr struct TestStruct2
x::Int
name::String
y
end
```
