```
@generate_static_methods numbers 1argfuns 2argfuns
```

This macro creates methods that return `Static` numbers when functions are called with only `Static` arguments.

The inputs should be a list of literal numbers that will be tested as inputs and outputs of all functions.

Optionally a fourth argument can give a list of numbers that will only be considered as results, but not as inputs.

Example:

```
@generate_static_methods (0, 1) (sin, cos) (+, -)
```

will create all the following method definitions:

```
sin(::StaticInteger{0}) = StaticInteger{0}()
cos(::StaticInteger{0}) = StaticInteger{1}()
+(::StaticInteger{0}, ::StaticInteger{0}) = StaticInteger{0}()
+(::StaticInteger{0}, ::StaticInteger{1}) = StaticInteger{1}()
+(::StaticInteger{1}, ::StaticInteger{0}) = StaticInteger{1}()
-(::StaticInteger{0}, ::StaticInteger{0}) = StaticInteger{0}()
-(::StaticInteger{1}, ::StaticInteger{0}) = StaticInteger{0}()
-(::StaticInteger{1}, ::StaticInteger{1}) = StaticInteger{1}()
```

(Note: The macro will run in the local scope. Functions from `Base` must be imported before they can be extended.)
