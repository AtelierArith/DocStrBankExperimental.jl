```
@insert_into_runhandlers outer_handler @syntax_eff begin
  # ...
end
```

Next to simple Effects which can be directly composed down to plain values and reconstructed again from plain values, there are also a couple of more elaborate Effects, which values cannot be extracted without providing further context.

Callables are a good example. It is impossible to extract the values of a callable without calling it, or without constructing another Callable around it.

With all these example the typical flow would be like

```julia

Callable(function (args...; kwargs...)
  callablehandler = CallableHandler(args...; kwargs...)

  SomeOtherNeededContext() do info
    otherhandler = SomeOtherHandler(info)

    # ... possibly further nestings

    @runhandlers (callablehandler, otherhandler #= possible further handlers =#) @syntax_eff begin
      # ...
    end
  end
end)
```

`@inser_into_runhandlers` can be used to simplify and even separate these outer handlers from one another, so that they can be used as composable interchangeable macros.

For example, here the implementation of `@runcallable` (ignoring macro hygiene)

```julia
macro runcallable(expr)
  :(Callable(function(args...; kwargs...)
    @insert_into_runhandlers(CallableHandler(args...; kwargs...), $expr)
  end))
end
```

This will search for an existing call to `runhandlers` within the given `expr`, and if found, inserts the CallableHandler similar to the motivating example above. If no `runhandlers` is found, it will create a new one.

This way, you can compose the nested code-structures very easily. You only have to be careful, that you always run all outer effects at once, in one single statement, so that `@insert_into_runhandlers` can actually find the right `runhandlers`.
