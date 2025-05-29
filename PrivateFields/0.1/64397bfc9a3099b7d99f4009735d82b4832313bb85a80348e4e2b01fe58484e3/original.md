```
@private_method ...
```

Tags the method which follows the macro as having privileged access to particular      fields for annotated types. This allows interacting with the type through     the traditional dot-syntax, `a.b`, rather than throwing an error.

Note that this replaces `a.b` with `PrivateFields.getproperty_direct(a, :b)`, so     property or field-retrieval should be handled there.

# Usage

Annotate the arguments in a method signature you wish to have privileged access to      with four colons: `::::`

See the definition of `f` in the example below

# Example

```@example
@private_struct struct Foo{X,Y}
    @private x::X
    y::Y
end

@private_method f(a::::Foo, b::Foo) = a.x + b.y

foo = Foo(1.0, 2.0)

@assert f(foo, foo) == 3.0

foo.x + foo.y # throws an error
```
